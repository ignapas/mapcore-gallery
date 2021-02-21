<template>
  <div class="indicator-container">
    <div
      v-for="(number, index) in count"
      :key="'indicator_' + number"
      :class="['indicator', { active: current === index }]"
    />
  </div>
</template>

<script>
export default {
  name: 'IndexIndicator',
  props: {
    count: {
      type: Number,
      default: 0
    },
    current: {
      type: Number,
      default: 0
    }
  }
}
</script>

<style scoped>
.indicator-container {
  display: flex;
  justify-content: center;
}
.indicator {
  width: 2rem;
  height: 0.125rem;
  margin-left: 0.25rem;
  margin-right: 0.25rem;
  background-color: #cccccc;
}
.indicator.active {
  background-color: #484848;
}
</style>
