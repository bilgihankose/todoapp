<template>
  <div class="todo">
    <form>
      <div class="form-group">
        <label for="addTodo">Add task</label>
        <input
          type="text"
          class="form-control"
          placeholder="Add task"
          id="addTodo"
          v-model="newTodo"
        />
        <button
          @click="addTodo"
          type="submit"
          class="btn d-inline-block btn-primary"
        >
          Add
        </button>
      </div>
    </form>

    <ul class="list-group" v-for="(todo, index) in todos" :key="index">
      <li
        class="list-group-item d-flex justify-content-between align-items-center"
      >
        {{ todo.title }}
        <button
          @click="removeTodo"
          type="submit"
          class="btn d-inline-block btn-danger"
        >
          Remove
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  data() {
    return {
      todos: [],
      newTodo: "",
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.length == 0) {
        return;
      }
      this.todos.push({
        id: this.todos.length + 1,
        title: this.newTodo,
        completed: false,
      });
      this.newTodo = "";
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>
