<script setup>
  const props = defineProps({
    isChecked: Boolean
  })
</script>

<template>
  <img src='https://dummyimage.com/100x100/ffffff/000000' alt='' :class="{ checked: isChecked }"/>
</template>

<style lang="scss" scoped>
  .checked {
    border: 5px solid green;
  }
</style>