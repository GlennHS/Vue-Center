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
    <div class="todo-checkbox-container">
      <Checkbox :is-checked="complete"/>
    </div>
    <div class="todo-basic-info">
      <span class="todo-title">{{ title }}</span>
      <span class="todo-desc">{{ desc.length > 80 ? desc.slice(0,80) + "..." : desc }}</span>
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
    margin: 10px 0;
    border-top: 2px solid var(--bg-2);
    border-bottom: 2px solid var(--bg-2);
    transition: 0.25s ease;
    cursor: pointer;

    .todo-checkbox-container {
      grid-area: c;
      display: flex;
      justify-content: flex-end;
      align-items: center;
      margin-right: 30px;
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

      .todo-title { font: var(--font-header); }
    }

    &:hover {
      transform: scale(1.05);
      
    }
  }
</style>
