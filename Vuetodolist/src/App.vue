<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import { reactive, ref, computed } from "vue";
import Sidebar from "./components/sidebar.vue";
import categories from "./components/categories.vue";
import todolist from "./components/todolist.vue";
import homeVue from "./home.vue";
import loginVue from "./login.vue";
import errorvue from "./non-existent-path.vue";

const routes = {
  "/": loginVue,
  "/home": homeVue,
  "/error": errorvue
};

const currentPath = ref(window.location.hash);

window.addEventListener("hashchange", () => {
  currentPath.value = window.location.hash;
});

const currentView = computed(() => {
  return routes[currentPath.value.slice(1) || "/"];
});
const nav = ref(false);

function toggle() {
  nav.value = !nav.value;
}
</script>

<template>
  <component :is="currentView" />
</template>

<style>
body {
  margin: 0;
  width: 100%;
  height: 100%;
  background-color: #f2f2f2;
  overflow: hidden;
  padding: 20px;
  padding-top: 50px;
  z-index: 0;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  overflow-y: scroll;
}
</style>
