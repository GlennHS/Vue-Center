<script setup>
import Checkbox from "./Checkbox.vue";
import { ref } from 'vue';
import Datepicker from '@vuepic/vue-datepicker';
import PriorityPicker from './PriorityPicker.vue';

const date = ref();

const props = defineProps({
  title: String,
  desc: String,
  priority: String,
  due: String,
  complete: Boolean,
  isActive: {
    type: Boolean,
    default: false
  }
})

const getToday = () => (new Date).toLocaleDateString('ko-KR')
</script>

<script>
const strikeMe = (ev) => {
  const choices = [
    "var(--color-cobalt-blue)",
    "var(--color-sunset-orange)",
    "var(--color-royal-purple)",
    "var(--color-bright-pink)"
  ]

  const chosenColor = choices[Math.floor(Math.random() * choices.length)]

  ev.target.closest(".todo-item").style.setProperty("--strike", chosenColor)
}
</script>

<template>
  <div class="todo-item" :class="{ done: complete, active: isActive }">
    <div class="todo-checkbox-container" @click="(ev) => { complete = !complete; strikeMe(ev); }">
      <div class="todo-checkbox-wrap">
        <Checkbox :is-checked="complete"/>
      </div>
    </div>
    <div class="todo-basic-info">
      <span class="todo-title">{{ title }}</span>
      <div class="todo-priority-wrap">
        <PriorityPicker v-if="!isActive" :priority="priority" :is-editable="isActive"/>
      </div>
      <span class="todo-desc">{{ desc.length > 110 ? desc.slice(0,110) + "..." : desc }}</span>
    </div>
    <div :class="{ open: isActive }" class="todo-expanded-info">
      <Datepicker
        v-model="due"
        v-if="due"
        auto-apply=""
        :closeOnAutoApply="false"
        :enableTimePicker="false"
        :monthChangeOnScroll="false"
      />
      <button v-else
        class="todo-due-button"
        @click="due = getToday()">
        Add Due Date
      </button>
      
      <PriorityPicker :priority="priority" :is-editable="isActive" @priority-change="(p) => priority = p"/>
    </div>
    <div @click="isActive = !isActive" class="todo-expander-bar">
      <i class="fa-solid fa-arrows-down-to-line"></i>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  .todo-item {
    --strike: var(--color-cobalt-blue); /* fallback if vue hook fails */
    width: 100%;
    margin: 30px 0;
    padding-top: 10px;
    display: grid;
    grid-template-areas: 'c d'
      'e e'
      'b b';
    grid-template-columns: 10% 90%;
    background: var(--bg-2);
    border-top: 2px solid $color-royal-purple;
    transition: transform 0.25s ease;

    .todo-checkbox-container {
      grid-area: c;
      display: flex;
      justify-content: right;
      align-items: center;
      margin: 20px 30px 20px 0;

      .todo-checkbox-wrap {
        background: white;
        height: 30px;
        width: 30px;
        padding: 0 0 5px 5px;
        display: flex;
        align-items: flex-start;
        justify-content: flex-start;
      }
    }

    .todo-basic-info {
      grid-area: d;
      display: grid;
      grid-template-areas: 't p'
        'd d';
      grid-template-columns: 70% 30%;
      row-gap: 10px;
      padding-bottom: 10px;
      justify-content: center;

      .todo-title {
        grid-area: t;
        font: $font-header;
        align-self: center
      }

      .todo-desc { grid-area: d; }
      .todo-priority-wrap {
        grid-area: p;
        width: 100%;
        display: flex;
        justify-content: right;

        .priority-picker {
          margin-right: 10px;
        }
      }
    }

    .todo-expanded-info {
      grid-area: e;
      max-height: 0;
      overflow: hidden;
      // transition: max-height 0.5s linear; //Disabling until I can make it look less jarring

      &.open {
        max-height: 100%;
        padding: 10px 20px 20px 20px;
      }
    }

    .todo-expander-bar {
      padding: 5px 0;
      background: $color-bright-pink;
      grid-area: b;
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 0 0 15px 15px;
      height: 100%;
      transition-property: height, border-radius;
      transition-duration: 0.25s;
      cursor: pointer;;
    }

    &.active .todo-expander-bar i {
      transform: rotate(180deg);
    }

    &:hover .todo-expander-bar {
      height: 130%;
      border-radius: 0 0 25px 25px;
    }

    &.done .todo-title {
      position: relative;
      display: inline-block;
      block-size: fit-content;
      width: fit-content;
    }

    &.done .todo-title::after {
      content: ' ';
      position: absolute;
      top: 50%;
      left: 0;
      width: 100%;
      height: 4px;
      background-color: var(--strike);
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
