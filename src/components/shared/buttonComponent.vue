<template>
    <button @click="state.handleClick">{{ state.buttonText }}</button>
</template>
<script setup>
import { defineProps, reactive } from 'vue';
const props = defineProps({
    data: Function
})

const state = reactive({
    timerStarted: false,
    buttonText: 'Start',
    handleClick: () => {
        if (!props.data) return
        state.timerStarted = !state.timerStarted
        if (state.timerStarted) state.buttonText = 'Stop'
        if (!state.timerStarted) state.buttonText = 'Start'
        props.data()
    }
})
</script>
<style>
</style>