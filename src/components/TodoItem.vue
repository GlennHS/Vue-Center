<script setup>
import Checkbox from "./Checkbox.vue";

const props = defineProps({
  title: String,
  desc: String,
  priority: String,
  due: String,
  complete: {
    type: Boolean,
    default: false
  }
})
</script>

<template>
  <div class="todo-item">
    <div class="todo-checkbox">
      <Checkbox :is-checked="complete"/>
    </div>
    <div class="todo-basic-info">
      <span class="todo-title">{{ title }}</span>
      <span class="todo-title">{{ desc.length > 80 ? desc.slice(0,80) + "..." : desc }}</span>
    </div>
    <div class="todo-details">

    </div>
  </div>
</template>

<style lang="scss" scoped>
  .todo-item {
    display: grid;
    grid-template-areas: 'c d';
    grid-template-columns: 20% 80%;

    .todo-checkbox {
      grid-area: c;
      text-align: right;
      padding-right: 30px;
      img {
        width: 20px;
      }
    }

    .todo-basic-info {
      grid-area: d;
      display: flex;
      flex-flow: column nowrap;
      justify-content: space-around;
      align-items: flex-start;
    }
  }
</style>
