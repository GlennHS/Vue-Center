<script setup>
  const props = defineProps({
    priority: {
      type: String,
      default: 'low'
    },
    isEditable: {
      type: Boolean,
      default: false
    }
  })

  function setPriority(newPriority) {
    if(isEditable) priority = newPriority;
  }

  function getPriority() { return priority; }
</script>

<template>
  <div class="priority-picker" :class="{ editable: isEditable}">
    <div class="priority low-priority"
      @click="() => { if(isEditable) priority = 'low'; $emit('priorityChange', 'low') }" :class="{selected : priority == 'low'}">
      <i class="fa-solid fa-info"></i>
      <span v-if="isEditable">Low</span>
    </div>
    <div class="priority med-priority"
      @click="() => { if(isEditable) priority = 'med'; $emit('priorityChange', 'med') }" :class="{selected : priority == 'med'}">
      <i class="fa-solid fa-exclamation"></i>
      <span v-if="isEditable">Med</span>
    </div>
    <div class="priority high-priority"
      @click="() => { if(isEditable) priority = 'high'; $emit('priorityChange', 'high')  }" :class="{selected : priority == 'high'}">
      <i class="fa-solid fa-triangle-exclamation"></i>
      <span v-if="isEditable">High</span>
    </div>
    <div class="priority critical-priority"
      @click="() => { if(isEditable) priority = 'critical'; $emit('priorityChange', 'critical')  }" :class="{selected : priority == 'critical'}">
      <i class="fa-solid fa-radiation"></i>
      <span v-if="isEditable">V. High</span>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  $color-priority-low: #42B3D5;
  $color-priority-med: #FFB507;
  $color-priority-high: #FF6800;
  $color-priority-vhigh: #D5001A;

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
      transition: box-shadow, background-color 0.33s;

      i {
        font-size: 24px;
      }

      &:first-child {
        border-left: none;
      }

      &.low-priority {
        background: $color-priority-low;

        &.selected { color: $color-priority-low; }
      }
      &.med-priority {
        background: $color-priority-med;

        &.selected { color: $color-priority-med; }
      }
      &.high-priority {
        background: $color-priority-high;

        &.selected { color: $color-priority-high; }
      }
      &.critical-priority {
        background: $color-priority-vhigh;

        &.selected { color: $color-priority-vhigh; }
      }

      &.selected { background: white; }

      &:hover {
        box-shadow: 0 0 5px #444 inset;
      }

      &:active, &.selected {
        box-shadow: 0 0 8px #121212 inset;

        * {
          transition: 0.25s;
          transform: translateY(3px);
        }
      }
    }

    &:not(.editable) {
      width: 200px;

      .priority {
        cursor: default;

        i {
          font-size: 20px;
        }

        &.selected * {
          transform: none;
        }

        &:hover {
          box-shadow: none;
        }

        &:active, &.selected {
          box-shadow: none;

          * {
            transform: none;
          }
        }
      }

    }
  }

</style>