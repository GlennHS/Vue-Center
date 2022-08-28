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
  $normal-scale: 1.3;

  .todo-checkbox {
    transform-origin: 0 100%;
    transform: scale($normal-scale);

    path {
      stroke-dasharray: 1000;
      stroke-dashoffset: 1000;
    }

    &.checked {

      path {
        animation: 2.5s swish forwards;
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
</style>