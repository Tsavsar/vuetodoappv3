<script setup>
import Sidebar from "./components/sidebar.vue";
import categories from "./components/categories.vue";
import todolist from "./components/todolist.vue";
</script>

<template>
  <Sidebar />
  <categories />
  <todolist />
</template>

<style>
body {
  margin: 0;
  width: 100%;
  height: 100%;
  background-color: #f2f2f2;
  overflow: hidden;
  padding: 20px;
  z-index: 0;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  /* overflow-y: scroll; */
}
</style>
