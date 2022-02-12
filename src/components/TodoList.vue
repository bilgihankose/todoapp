<template>
  <div>
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
          @click="getId(index)"
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
  name: "TodoList",
  props: {
    todos: {
      type: Array,
    },
  },
  methods: {
    getId(id) {
      this.$emit("todoID", id);
    },
    toggleTodo(todo) {
      todo.completed = !todo.completed;
    },
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
