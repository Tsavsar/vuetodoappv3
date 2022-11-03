<script setup>
import { reactive, ref } from "vue";
import todolistVue from "./todolist.vue";
import dayjs from "dayjs";
import relativeTime from "dayjs/plugin/relativeTime.js";

// dayjs.updateLocale("en", {
//   relativeTime: {
//     future: "in %s",
//     past: "%s ago",
//     s: "a few seconds",
//     m: "a minute",
//     mm: "%d minutes",
//     h: "an hour",
//     hh: "%d hours",
//     d: "a day",
//     dd: "%d days",
//     M: "a month",
//     MM: "%d months",
//     y: "a year",
//     yy: "%d years"
//   }
// });

const open = ref(false);

function toggle() {
  open.value = !open.value;
}

const userData = JSON.parse(localStorage.getItem("userData"));

const fromdate = userData.date;

dayjs.extend(relativeTime);

var times = dayjs(fromdate).fromNow();

const openmenu = ref("open");
</script>

<template>
  <div class="menu" @click="toggle()">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512">
      <path
        d="M0 96C0 78.3 14.3 64 32 64H416c17.7 0 32 14.3 32 32s-14.3 32-32 32H32C14.3 128 0 113.7 0 96zM0 256c0-17.7 14.3-32 32-32H416c17.7 0 32 14.3 32 32s-14.3 32-32 32H32c-17.7 0-32-14.3-32-32zM448 416c0 17.7-14.3 32-32 32H32c-17.7 0-32-14.3-32-32s14.3-32 32-32H416c17.7 0 32 14.3 32 32z"
      />
    </svg>
  </div>
  <Transition name="slide-fade">
    <template v-if="open">
      <div class="side-bar">
        <!-- <a href="#/">
          <button>Send me login!</button>
        </a> -->
        <div class="profile-cont">
          <h1 class="username">
            {{ userData.username }}
            {{ userData.timenow }}
            <br />
            {{ times }}
          </h1>
        </div>
        <div class="setting" @click="toggle()">
          <div class="white move">
            <svg width="32" height="32" viewBox="0 0 24 24">
              <path
                d="M6.4 19L5 17.6l5.6-5.6L5 6.4L6.4 5l5.6 5.6L17.6 5L19 6.4L13.4 12l5.6 5.6l-1.4 1.4l-5.6-5.6Z"
              />
            </svg>
          </div>
          <br />
          <div class="white">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              id="Outline"
              viewBox="0 0 24 24"
              width="25"
              height="25"
            >
              <path
                d="M1,4.75H3.736a3.728,3.728,0,0,0,7.195,0H23a1,1,0,0,0,0-2H10.931a3.728,3.728,0,0,0-7.195,0H1a1,1,0,0,0,0,2ZM7.333,2a1.75,1.75,0,1,1-1.75,1.75A1.752,1.752,0,0,1,7.333,2Z"
              />
              <path
                d="M23,11H20.264a3.727,3.727,0,0,0-7.194,0H1a1,1,0,0,0,0,2H13.07a3.727,3.727,0,0,0,7.194,0H23a1,1,0,0,0,0-2Zm-6.333,2.75A1.75,1.75,0,1,1,18.417,12,1.752,1.752,0,0,1,16.667,13.75Z"
              />
              <path
                d="M23,19.25H10.931a3.728,3.728,0,0,0-7.195,0H1a1,1,0,0,0,0,2H3.736a3.728,3.728,0,0,0,7.195,0H23a1,1,0,0,0,0-2ZM7.333,22a1.75,1.75,0,1,1,1.75-1.75A1.753,1.753,0,0,1,7.333,22Z"
              />
            </svg>
          </div>
          <!-- width="35px" height="35px" -->
          <br />
          <a href="#/">
            <div class="white">
              <svg width="32" height="32" viewBox="0 0 24 24">
                <path
                  d="M3 5c0-1.1.9-2 2-2h8v2H5v14h8v2H5c-1.1 0-2-.9-2-2V5Zm14.176 6L14.64 8.464l1.414-1.414l4.95 4.95l-4.95 4.95l-1.414-1.414L17.176 13H10.59v-2h6.586Z"
                />
              </svg>
            </div>
          </a>
        </div>
      </div> </template
  ></Transition>
</template>
<script>
import child from "./todolist.vue";
// export default{
//     name: 'app',
</script>

<style scoped>
.move {
  margin-left: -5px;
}
.slide-fade-enter-active {
  transition: all 1s ease-out;
}

.slide-fade-leave-active {
  transition: all 1s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(-1000px);
  opacity: 1;
}
.side-bar {
  background-color: #008dff;
  border-radius: 0px 35px 0px 0px;
  height: 100%;
  width: 80%;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1;
  overflow-x: hidden;
  overflow-y: hidden;
  transition: 0.5s;
}
.profile-cont {
  color: #ffffff;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding-top: 160px;
}
.username {
  font-weight: 600;
  font-size: 32px;
  font-family: "Inter";
  font-style: normal;
  font-weight: 600;
  line-height: 39px;
  color: #ffffff;
}
.tasks,
.comp-tasks {
  font-weight: 600;
  font-size: 20px;
  font-family: "Inter";
  font-style: normal;
  font-weight: 600;
}
.setting {
  margin-top: 155%;
  margin-left: 20px;
  bottom: 20px;
  position: fixed;
}
.white {
  fill: #ffffff;
  width: 35px;
  height: fit-content;
}

.menu {
  width: 20px;
  height: 10px;
  fill: #808080;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  overflow: hidden;
}
</style>
