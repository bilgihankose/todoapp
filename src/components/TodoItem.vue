<template>
  <div class="todo">
    <h1>Todoeli</h1>
    <form @submit.prevent="addTodo">
      <div class="form-group">
        <label for="addTodo">Add New Todo</label>
        <input
          type="text"
          class="form-control"
          placeholder="e.g., Buy gift tomorrow"
          id="addTodo"
          v-model="newTodo"
          autocomplete="off"
        />
        <button
          @click="addTodo"
          type="submit"
          class="btn d-inline-block btn-primary mt-3"
        >
          Add
        </button>
      </div>
    </form>
    <hr />
    <h3>Todo List</h3>
    <todo-list :todos="todos" @todoID="removeTodo"></todo-list>
  </div>
</template>

<script>
import TodoList from "./TodoList.vue";

export default {
  components: {
    TodoList,
  },
  name: "TodoItem",

  data() {
    return {
      todos: [],
      completedTodos: [],
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
    removeTodo(ID) {
      this.todos.splice(ID, 1);
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
