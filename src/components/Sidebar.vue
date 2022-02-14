<template>
  <div class="left-menu">
    <div class="list-holder">
      <div class="top-filter-container">
        <ul v-for="(item, key) in items" :key="key" class="top-filters">
          <li class="item">{{ item.name }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Sidebar",
  data() {
    return {
      items: [
        {
          name: "Inbox",
          icon: "dashboard",
          path: "/inbox",
        },
        {
          name: "Today",
          icon: "users",
          path: "/today",
        },
        {
          name: "Upcoming",
          icon: "cog",
          path: "/upcoming",
        },
        {
          name: "Filters & Labels",
          icon: "cog",
          path: "/upcoming",
        },
      ],
    };
  },
};
</script>

<style scoped>
.left-menu {
  box-sizing: border-box;
  width: 305px;
  height: 100vh;
  background-color: #282828;
  padding-left: 35px;
  position: fixed;
  left: 0;
  top: 0;
  color: white;
}

.item {
  padding: 5px 16px 5px 5px;
  list-style: none;
}

.top-filter-container {
  margin-top: 100px;
}
</style>
