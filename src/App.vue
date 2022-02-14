<template>
  <div>
    <Navbar></Navbar>
    <div class="container mt-5">
      <todo-item></todo-item>
    </div>
  </div>
</template>

<script>
import TodoItem from "./components/TodoItem.vue";
import Navbar from "./components/Navbar.vue";

export default {
  name: "App",
  components: {
    TodoItem,
    Navbar,
  },
};
</script>

<style scoped>
.container {
  margin-left: 305px;
}
</style>
