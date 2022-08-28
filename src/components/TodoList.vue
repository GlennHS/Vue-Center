<script setup>
import TodoItem from './TodoItem.vue'

const todos = [
  {
    title: "Item A",
    desc: "lorem ipsum dolor sit amet consectetur adipiscing elit non nobis domine veni vidi vici.",
    priority: "low",
    due: "2022-08-30",
    complete: false
  },
  {
    title: "Item B",
    desc: "lorem ipsum dolor sit amet consectetur adipiscing elit non nobis domine veni vidi vici. lorem ipsum dolor sit amet consectetur adipiscing elit non nobis domine veni vidi vici.",
    priority: "med",
    due: "2022-09-22",
    complete: false
  },
  {
    title: "Item C",
    desc: "lorem ipsum dolor sit amet consectetur adipiscing elit non nobis domine veni vidi vici.",
    priority: "high",
    due: "",
    complete: true
  }
]
</script>

<template>
  <div class="todo-list" v-for="todo in todos">
    <TodoItem v-bind="todo" />
  </div>
</template>

<style scoped>
  .todo-list {
    width:100%;
  }
</style>
