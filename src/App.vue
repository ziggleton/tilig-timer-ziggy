<template>
  <title-component :data="state.title"></title-component>
  <time-indicator-component :data="state.time"></time-indicator-component>
  <button-component :data="toggleTimer"></button-component>
</template>
<script setup>
import { reactive } from 'vue';
import titleComponent from './components/shared/titleComponent.vue';
import buttonComponent from './components/shared/buttonComponent.vue';
import timeIndicatorComponent from './components/shared/timeIndicatorComponent.vue';

const state = reactive({
  title: "Stop Watch",
  hasStarted: false,
  timer: null,
  time: 0
})

const toggleTimer = () => {
  state.hasStarted = !state.hasStarted
  if (state.hasStarted) startTimer()
  if (!state.hasStarted) stopTimer()
}

const startTimer = () => {
  state.title = 'started timer'
  state.timer = setInterval(() => {
    state.time += 100
  }, 100)
}

const stopTimer = () => {
  state.title = 'stopped timer'
  clearInterval(state.timer)
}

</script>
<style>
</style>
