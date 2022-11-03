<script setup>
import dayjs from "dayjs";
import NotFound from "./NotFound.vue";
import { ref, computed } from "vue";

import relativeTime from "dayjs/plugin/relativeTime.js";

let id = 0;
const routes = {};

const now = new Date();

const userData = JSON.parse(localStorage.getItem("userData"));

const dateFormatted = dayjs(now).format("dddd, MMMM D");

const currentPath = ref(window.location.hash);

window.addEventListener("hashchange", () => {
  currentPath.value = window.location.hash;
});

const currentView = computed(() => {
  return routes[currentPath.value.slice(1) || "/"] || NotFound;
});

function openup() {
  location.href = "#/error";
}
</script>

<template>
  <div class="">
    <h3>Welcome Back {{ userData.username }}!</h3>

    <h4>{{ dateFormatted }}</h4>
  </div>
  <div class="categories">
    <h2>Categories</h2>
    <br />
    <div class="tabs">
      <a @click="openup">
        <div class="list 1">
          <p>Shopping List</p>
        </div>
      </a>

      <a @click="openup">
        <div class="list 2">
          <p>Gym Workouts</p>
        </div></a
      >

      <a @click="openup">
        <div class="list 3">
          <p>Shopping</p>
        </div>
      </a>
    </div>
  </div>
</template>

<style scoped>
a {
  text-decoration: none;
  color: none;
}
.fixed {
  position: fixed;
  top: 10px;
  z-index: 5;
}
.list {
  background: #ffffff;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  border-radius: 20px;
  margin-right: 19px;
  width: 155px;
  height: 108px;
  padding: 18px;
}

p {
  font-family: "Inter";
  font-style: normal;
  font-weight: 700;
  font-size: 24px;
  line-height: 29px;
  width: fit-content;
  color: #000000;
}
.task-num {
  bottom: 0px;
  font-family: "Inter";
  font-style: normal;
  font-weight: 400;
  font-size: 11px;
  line-height: 13px;

  color: #808080;
}

.tabs {
  height: 110px;
  width: 503px;
  display: flex;
  flex-direction: row;
  overflow-x: scroll;
  overflow-y: hidden;
  margin-top: 10px;
}

.categories {
  width: 100%;
  height: fit-content;
  overflow: scroll;
  margin-top: 40px;
}

h3 {
  font-family: "Inter";
  font-style: normal;
  font-weight: 600;
  font-size: 32px;
  line-height: 39px;
  color: #2f2f2f;
}

h4 {
  font-family: "Inter";
  font-style: normal;
  font-weight: 600;
  font-size: 20px;
  line-height: 39px;
  color: #2f2f2f;
}

h2 {
  width: fit-content;
  padding-left: 25px;
  margin-bottom: 20px;
  position: absolute;
  height: 21px;
  font-family: "Inter";
  font-style: normal;
  font-weight: 700;
  font-size: 15px;
  line-height: 18px;
  text-transform: uppercase;

  color: #808080;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  overflow: hidden;
}
</style>
