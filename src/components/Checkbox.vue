<script setup>
  const props = defineProps({
    isChecked: Boolean
  })
</script>

<template>
  <!-- <div :class="{ checked: isChecked }" @click="isChecked = !isChecked" class="todo-checkbox"/> -->
<svg
  :class="{ checked: isChecked }" class="todo-checkbox"
  viewBox="160.46 38.84 65 70" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:bx="https://boxy-svg.com">
  <defs>
    <linearGradient id="gradient-1" bx:pinned="true">
      <title>Center-Main</title>
      <stop offset="0" style="stop-color: rgb(8, 100, 228);"></stop>
      <stop offset="0.678" style="stop-color: rgb(172, 25, 219);"></stop>
      <stop offset="1" style="stop-color: rgb(238, 46, 165);"></stop>
    </linearGradient>
    <linearGradient id="gradient-1-0" gradientUnits="userSpaceOnUse" x1="253.102" y1="184.444" x2="253.102" y2="241.731" gradientTransform="matrix(1, 0, 0, 1, -60.025558, -140.059631)" xlink:href="#gradient-1"></linearGradient>
  </defs>
  <path style="fill: none; stroke-linecap: round; stroke-linejoin: round; stroke-width: 10px; stroke: url(#gradient-1-0);" d="M 166.642 82.162 C 168.937 84.328 185.455 102.678 184.418 101.608 C 185.469 101.871 219.419 44.384 219.419 44.384"></path>
</svg>
</template>

<style lang="scss" scoped>
  .todo-checkbox {
    transform-origin: 0 100%;
    transform: scale(1.3);

    path {
      stroke-dasharray: 1000;
      stroke-dashoffset: 1000;
    }

    &.checked {

      path {
        animation: 2.5s swish forwards,
          pop 1s forwards;
      }
    }
  }

  @keyframes swish {
    from {
      stroke-dashoffset: 1000;
    }
    to {
      stroke-dashoffset: 0;
    }
  }

  @keyframes pop {
    0% {
      width: 90%;
      height: 90%;
    }

    50% {
      width: 90%;
      height: 90%;
    }

    70% {
      width: 90%;
      height: 90%;
    }

    90% {
      width: 100%;
      height: 100%;
    }

    100% {
      width: 90%;
      height: 90%;
    }
  }
</style>