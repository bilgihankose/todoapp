<template>
  <div class="left-menu">
    <div class="list-holder">
      <div class="top-filter-container">
        <ul v-for="(item, key) in items" :key="key" class="top-filters">
          <li class="item">
            <span><i :class="item.icon"></i></span>
            <span class="pl-3">{{ item.name }}</span>
          </li>
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
          icon: "bi bi-envelope",
          path: "/inbox",
        },
        {
          name: "Today",
          icon: "bi bi-calendar-date",
          path: "/today",
        },
        {
          name: "Upcoming",
          icon: "bi bi-calendar-event",
          path: "/upcoming",
        },
        {
          name: "Filters & Labels",
          icon: "bi bi-grid",
          path: "/filters-and-labels",
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
