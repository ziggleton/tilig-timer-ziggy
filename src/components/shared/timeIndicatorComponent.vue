<template>
    <div id="time-indicator">{{ state.formattedTime }}</div>
</template>
<script setup>
import moment from 'moment'
import { computed, defineProps, reactive } from 'vue';
const props = defineProps({
    data: Number
})
const state = reactive({
    formattedTime: computed(() => {
        return formatTime(props.data)
    }),
    timeElapsed: 0
})

const formatTime = (time) => {
    if (!time) return
    const cDate = new Date()
    return moment(cDate).startOf('day').seconds(time).format('HH:mm:ss')
}
</script>
<style>
</style>