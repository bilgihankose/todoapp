<template>
  <div class="todo">
    <h1>Todo List</h1>
    <form @submit.prevent="addTodo">
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
          class="btn d-inline-block btn-primary mt-3"
        >
          Add todo
        </button>
      </div>
    </form>

    <ul v-if="todos.length > 0" class="list-group">
      <li
        v-for="(todo, index) in todos"
        :key="index"
        class="list-group-item d-flex justify-content-between align-items-center"
        :class="{ completed: todo.completed }"
        @click="$set((todo.completed = !todo.completed))"
      >
        <span> {{ todo.title }}</span>
        <button
          @click="removeTodo(index)"
          type="submit"
          class="btn d-inline-block btn-danger"
        >
          Remove
        </button>
      </li>
    </ul>

    <ul v-else class="list-group">
      <li class="list-group-item">
        <span>No tasks</span>
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
  watch: {
    todos: {
      handler() {
        localStorage.setItem("todos", JSON.stringify(this.todos));
      },
      deep: true,
    },
  },
  mounted: function () {
    if (localStorage.getItem("todos")) {
      this.todos = JSON.parse(localStorage.getItem("todos"));
    }
  },
};
</script>

<style scoped>
.completed {
  background: #f2f2f2;
}

.completed span {
  text-decoration: line-through;
}
</style>
