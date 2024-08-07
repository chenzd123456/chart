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
  initChart()
})

onUpdated(() => {
  updateChart()
})

const initChart = () => {
  chart = new Chart(chart_canvas_ref.value, props.config)
  console.log('ChartCanvas draw')
}

const updateChart = () => {
  chart.update()
}
</script>
