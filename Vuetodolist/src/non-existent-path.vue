<script setup>
import errors from "./components/NotFound.vue";
import backhomeVue from "./components/backhome.vue";
</script>

<template>
  <backhomeVue />
  <div class="mid">
    <errors />
    <h1 class="nothing">Nothing to see here........Yet</h1>
  </div>
</template>

<style>
.mid {
  margin-top: 40%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.nothing {
  font-family: "Inter";
  font-style: normal;
  font-weight: 400;
  text-align: center;
  font-size: 15px;
  line-height: 18px;
  color: #808080;
  display: flex;
  align-items: center;
  justify-content: center;
}

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
