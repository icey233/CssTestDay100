<template>
  <div :class="{ frame: true }">
    <div
      :class="{ menu: true, active: active1, paused: paused1 }"
      @click="toggleMenu"
    >
      <div class="one"></div>
      <div class="two"></div>
    </div>
    <div
      :class="{ menuitems: true, active: active2, paused: paused2 }"
      @click="changchun"
    >
      <ul>
        <li><span>Home</span></li>
        <li><span>Work</span></li>
        <li><span>Life</span></li>
        <li><span>Spirit</span></li>
      </ul>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
const active1 = ref(false);
const paused1 = ref(true);
const active2 = ref(false);
const paused2 = ref(false);
const toggleMenu = () => {
  active1.value = true
  paused1.value = false
  active2.value = true
  paused2.value = false 
};
const changchun = () => {
  active1.value = false;
  active2.value = false
};
</script>

<style lang="less" scoped>
@import url(https://fonts.googleapis.com/css?family=Open+Sans:600);
.frame {
  width: 20rem;
  height: 20rem;
  border-radius: 10px;
  box-shadow: 0 0 10px 5px #4a627a;
  background-color: #4a627a;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  .menu {
    position: absolute;
    top: 50%;
    left: 50%;
    z-index: 2;
    height: 1rem;
    width: 3rem;
    transform: translate(-50%, -50%);
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-direction: column;
    cursor: pointer;
    &.active {
      pointer-events: none;
      .one {
        animation: line-top-open 1s ease both;
      }
      .two {
        animation: line-bottom-open 1s ease both;
      }
    }
    &.paused {
      .one .two {
        animation: none;
      }
      .one {
        animation: line-top-close 1s ease both;
      }
      .two {
        animation: line-bottom-close 1s ease both;
      }
    }
    .one {
      width: 50px;
      height: 3px;
      background-color: white;
      animation: line-top-close 1s ease both;
    }
    .two {
      .one();
      animation: line-bottom-close 1s ease both;
    }
  }
  .menuitems {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    opacity: 0;
    &.active {
      opacity: 1;
      pointer-events: all;
      transition: all 0.5s ease-in-out 0.5s;
    }
    ul {
      list-style: none;
      display: flex;
      justify-content: space-between;
      align-items: end;
      padding: 0;
      li {
        span {
          color: white;
          font-family: "Open Sans", sans-serif;
          font-weight: 600;
          margin: 10px;
          &:hover {
            opacity: 0.6;
          }
        }
      }
    }
  }
}

@keyframes line-top-open {
  0% {
    transform: translate3d(0, 0, 0) scaleY(1) scaleX(1);
  }
  20% {
    transform: translate3d(0, 3px, 0) scaleY(1) scaleX(1);
  }
  40% {
    transform: translate3d(0, -20px, 0) scaleY(0.5) scaleX(1);
  }
  100% {
    transform: translate3d(0, -20px, 0) scaleY(0.5) scaleX(6);
  }
}

@keyframes line-bottom-open {
  0% {
    transform: translate3d(0, 0, 0) scaleY(1) scaleX(1);
  }
  20% {
    transform: translate3d(0, -3px, 0) scaleY(1) scaleX(1);
  }
  40% {
    transform: translate3d(0, 20px, 0) scaleY(0.5) scaleX(1);
  }
  100% {
    transform: translate3d(0, 20px, 0) scaleY(0.5) scaleX(6);
  }
}

@keyframes line-top-close {
  0% {
    transform: translate3d(0, -20px, 0) scaleY(0.5) scaleX(6);
  }
  60% {
    transform: translate3d(0, -20px, 0) scaleY(0.5) scaleX(1);
  }
  100% {
    transform: translate3d(0, 0, 0) scaleY(1) scaleX(1);
  }
}

@keyframes line-bottom-close {
  0% {
    transform: translate3d(0, 20px, 0) scaleY(0.5) scaleX(6);
  }
  60% {
    transform: translate3d(0, 20px, 0) scaleY(0.5) scaleX(1);
  }
  100% {
    transform: translate3d(0, 0, 0) scaleY(1) scaleX(1);
  }
}
</style>
