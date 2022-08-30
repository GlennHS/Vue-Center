<script setup>
import TodoItem from './TodoItem.vue'

const todos = [
  {
    title: "Go out and pet more cats",
    desc: "I've found that my life is lacking in feline companionship. Therefore I have decided to go out and find the biggest, cutest, cuddliest cat I can and befriend it. After which I shall bring it home and feed it all the fish it wants",
    priority: "critical",
    due: "2000-01-01",
    complete: false
  },
  {
    title: "This todo list item is a very long one and as such demands a very long title",
    desc: "lorem ipsum dolor sit amet consectetur adipiscing elit non nobis domine veni vidi vici. lorem ipsum dolor sit amet consectetur adipiscing elit non nobis domine veni vidi vici. lorem ipsum dolor sit amet consectetur adipiscing elit non nobis domine veni vidi vici. lorem ipsum dolor sit amet consectetur adipiscing elit non nobis domine veni vidi vici.",
    priority: "low",
    due: "2022-09-22",
    complete: true
  },
  {
    title: "Get good at Vue",
    desc: "I'm trying! It ain't easy but I'm getting there!",
    priority: "med",
    due: "",
    complete: false
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
