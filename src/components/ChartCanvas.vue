<template>
  <div>
    <canvas ref="chart_canvas_ref"></canvas>
  </div>
</template>

<script setup>
import { onMounted, onUpdated, ref } from 'vue'
import Chart from 'chart.js/auto'

const props = defineProps(['config'])

const chart_canvas_ref = ref()

let chart

onMounted(() => {
  chart = new Chart(chart_canvas_ref.value, props.config)
})

onUpdated(() => {
  chart.resize()
})
</script>
