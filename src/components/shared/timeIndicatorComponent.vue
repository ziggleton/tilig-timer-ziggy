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
    })
})

const formatTime = (time) => {
    const cDate = new Date()
    if (!time) return moment(cDate).startOf('day').millisecond(0).format('mm:ss:SS')
    return moment(cDate).startOf('day').millisecond(time).format('mm:ss:SS')
}
</script>
<style>
</style>