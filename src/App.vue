<template>
  <div>
    <Sidebar></Sidebar>
    <div class="container mt-5">
      <todo-item></todo-item>
    </div>
  </div>
</template>

<script>
import TodoItem from "./components/TodoItem.vue";
import Sidebar from "./components/Sidebar.vue";

export default {
  name: "App",
  components: {
    TodoItem,
    Sidebar,
  },
};
</script>

<style scoped>
.container {
  margin-left: 305px;
}
</style>
