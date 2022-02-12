<template>
  <div id="app">
    <div class="container mt-5">
      <todo-item></todo-item>
    </div>
  </div>
</template>

<script>
import TodoItem from "./components/TodoItem.vue";
export default {
  name: "App",
  components: {
    TodoItem,
  },
};
</script>
