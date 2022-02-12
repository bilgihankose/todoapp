<template>
  <div class="todo">
    <h1>Todo List</h1>
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

    <ul v-if="todos.length > 0" class="list-group">
      <li
        v-for="(todo, index) in todos"
        :key="index"
        class="list-group-item d-flex align-items-center"
        :class="{ completed: todo.completed }"
        title="Click for check todo completed!"
      >
        <input
          type="checkbox"
          class="mr-2 cursor-pointer"
          v-model="todo.completed"
          @click="toggleTodo(todo)"
        />
        <span>
          {{ todo.title }}
        </span>
        <button
          @click="removeTodo(index)"
          type="submit"
          class="btn d-inline-block ml-auto btn-danger"
        >
          Remove
        </button>
      </li>
    </ul>

    <ul v-else class="list-group">
      <li class="list-group-item bg-light">
        <span>There is no todo. Enjoy your day off!</span>
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
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
    toggleTodo(todo) {
      todo.completed = !todo.completed;
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
.cursor-pointer {
  cursor: pointer;
}
</style>
