<script setup>
import Checkbox from "./Checkbox.vue";
import { ref } from 'vue';
import Datepicker from '@vuepic/vue-datepicker';
    
const date = ref();

const props = defineProps({
  title: String,
  desc: String,
  priority: String,
  due: String,
  complete: Boolean
})
</script>

<script>
const strikeMe = (ev) => {
  const choices = [
    "var(--theme-1)",
    "var(--theme-2)",
    "var(--theme-3)",
    "var(--theme-4)"
  ]

  const chosenColor = choices[Math.floor(Math.random() * choices.length)]

  ev.target.closest(".todo-item").style.setProperty("--strike", chosenColor)
}
</script>

<template>
  <div class="todo-item" :class="{ done: complete }">
    <div class="todo-checkbox-container" @click="(ev) => { complete = !complete; strikeMe(ev); }">
      <Checkbox :is-checked="complete"/>
    </div>
    <div class="todo-basic-info">
      <span class="todo-title">{{ title }}{{ due ? " || " + due : "" }}</span>
      <span class="todo-desc">{{ desc.length > 80 ? desc.slice(0,80) + "..." : desc }}</span>
    </div>
    <div class="todo-details">
      <Datepicker />
    </div>
  </div>
</template>

<style lang="scss" scoped>
  .todo-item {
    --strike: var(--theme-1); /* fallback if vue hook fails */
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
      justify-content: center;
      align-items: center;
      margin-right: 30px;
      background: white;
    }

    .todo-basic-info {
      grid-area: d;
      display: flex;
      flex-flow: column nowrap;
      justify-content: space-around;
      align-items: flex-start;

      .todo-title { font: var(--font-header); }
    }

    &.done span {
      position: relative;
    }

    &.done span:first-child::after {
      content: ' ';
      position: absolute;
      top: 50%;
      left: 0;
      width: 100%;
      height: 4px;
      background: var(--strike);
      animation: 0.5s strike linear forwards;
    }

    &:hover {
      transform: scale(1.05);
    }

    @keyframes strike{
      0%   { width : 0; }
      100% { width: 100%; }
    }
  }
</style>
