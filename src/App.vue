<script setup>
import TodoList from './components/TodoList.vue';
import '@vuepic/vue-datepicker/dist/main.css'

</script>

<template>
  <div class="app-container">
    <TodoList></TodoList>
  </div>
</template>

<style scoped>
  .app-container {
    width: 1000px;
  }
</style>
