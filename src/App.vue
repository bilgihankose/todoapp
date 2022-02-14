<template>
  <div>
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

<style scoped>
.container {
  margin-left: 305px;
}
</style>
