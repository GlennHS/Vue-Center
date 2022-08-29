<script setup>
  const props = defineProps({
    priority: {
      type: String,
      default: 'low'
    }
  })
</script>

<script>
  // switch (priority) {
  //   case 'low':
      
  //     break;
  //   case 'med':
      
  //     break;
  //   case 'high':
      
  //     break;
  //   case 'critical':
      
  //     break;

  //   default:
  //     break;
  // }
</script>

<template>
  <div class="priority-picker">
    <div class="priority low-priority">
      <i class="fa-solid fa-triangle-exclamation"></i>
      <span>Low</span>
    </div>
    <div class="priority med-priority">
      <i class="fa-solid fa-triangle-exclamation"></i>
      <span>Med</span>
    </div>
    <div class="priority high-priority">
      <i class="fa-solid fa-triangle-exclamation"></i>
      <span>High</span>
    </div>
    <div class="priority critical-priority">
      <i class="fa-solid fa-triangle-exclamation"></i>
      <span>V. High</span>
    </div>
  </div>
  {{ priority }}
</template>

<style lang="scss" scoped>
  $color-priority-low: #58f;
  $color-priority-med: #ff3;
  $color-priority-high: #f93;
  $color-priority-vhigh: #f33;

  .priority-picker {
    border-radius: 20px;
    border: 5px solid black;
    width: 300px;
    overflow: hidden;
    display: grid;
    grid-template-columns: repeat(4,1fr);

    .priority {
      display: flex;
      flex-flow: column nowrap;
      justify-content: center;
      align-items: center;
      padding: 5px 15px;
      color: #232323;
      font: bolder 13px/1.2 'Alumni Sans Regular';
      cursor: pointer;
      border-left: 2px solid black;
      transition: box-shadow 0.33s;

      &:first-child {
        border-left: none;
      }

      &.low-priority {
        background: $color-priority-low;
      }
      &.med-priority {
        background: $color-priority-med;
      }
      &.high-priority {
        background: $color-priority-high;
      }
      &.critical-priority {
        background: $color-priority-vhigh;
      }

      &:hover {
        box-shadow: 0 0 5px #444 inset;
      }

      &:active {
        box-shadow: 0 0 8px #121212 inset;

        * {
          transition: 0.25s;
          transform: translateY(3px);
        }
      }
    }

    i {
      font-size: 24px;
    }
  }

</style>