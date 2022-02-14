<template>
  <div>
    <Sidebar></Sidebar>
    <nav class="navbar text-white bg-dark">
      <!-- Navbar content -->
      <div class="nav-list">
        <div class="left-side">
          <span class="ml-4 hamburger">
            <i class="bi bi-list align-middle" style="font-size: 2rem"></i>
          </span>
          <span class="ml-2">
            <i
              class="bi bi-house-door align-middle"
              style="font-size: 1.5rem"
            ></i>
          </span>
          <div class="input-group ml-3 for-position">
            <div class="input-group-prepend">
              <span class="input-group-text" id="basic-addon1">@</span>
            </div>
            <input
              type="text"
              class="form-control"
              placeholder="Search"
              aria-label="Search"
              aria-describedby="basic-addon1"
            />
          </div>
        </div>
        <div class="right-side">
          <span class="">
            <i
              class="bi bi-person-circle align-middle"
              style="font-size: 2rem"
            ></i>
          </span>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
import Sidebar from "./Sidebar.vue";

export default {
  name: "Navbar",
  components: {
    Sidebar,
  },
};
</script>

<style scoped>
.for-position {
  position: fixed;
  top: 13px;
  left: 100px;
  width: 180px;
}
.right-side {
  position: fixed;
  top: 12px;
  right: 100px;
}
</style>
