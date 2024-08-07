<template>
  <el-container class="w-full h-full">
    <el-row class="w-full h-full">
      <el-col :span="12">
        <CodeEditor language="json" v-model="json"></CodeEditor>
      </el-col>
      <el-col :span="12">
        <ChartCanvas :config="config"></ChartCanvas>
      </el-col>
    </el-row>
  </el-container>
</template>

<script setup>
import CodeEditor from '@/components/CodeEditor.vue'
import ChartCanvas from '@/components/ChartCanvas.vue'

import { ref, computed } from 'vue'

const json = ref(
  `[
    { "year": 2010, "count": 10 },
    { "year": 2011, "count": 20 },
    { "year": 2012, "count": 15 },
    { "year": 2013, "count": 25 },
    { "year": 2014, "count": 22 },
    { "year": 2015, "count": 30 },
    { "year": 2016, "count": 28 }
]`
)

const data = computed(() => {
  return JSON.parse(json.value)
})

const config = computed(() => {
  console.log('config update')
  return {
    type: 'bar',
    data: {
      labels: data.value.map((row) => row.year),
      datasets: [
        {
          label: 'Acquisitions by year',
          data: data.value.map((row) => row.count)
        }
      ]
    }
  }
})
</script>
