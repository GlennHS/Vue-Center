<script setup>
  const props = defineProps({
    isChecked: Boolean
  })
</script>

<template>
  <div :class="{ checked: isChecked }" @click="isChecked = !isChecked" class="todo-checkbox"/>
</template>

<style lang="scss" scoped>
  .todo-checkbox {
    width: 50px;
    height: 50px;
    background-image: url('https://dummyimage.com/50x50/ffffff/ffffff');

    &.checked {
      background-image: url('https://dummyimage.com/50x50/99ff99/000000')
    }
  }
</style>