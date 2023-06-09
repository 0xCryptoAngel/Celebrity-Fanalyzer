<template>
  <v-chart class="chart" :option="option" autoresize />
</template>

<script setup>
import { BarChart } from 'echarts/charts'
import { GridComponent, TitleComponent, TooltipComponent } from 'echarts/components'
import { use } from 'echarts/core'
import { CanvasRenderer } from 'echarts/renderers'
import { onBeforeMount, onBeforeUpdate, ref } from 'vue'
import VChart from 'vue-echarts'

use([CanvasRenderer, BarChart, GridComponent, TitleComponent, TooltipComponent])

const props = defineProps({
  data: { type: Object, required: true },
  title: { type: String, required: false }
})

let dislikes = []
let likes = []
let periode = []
let stats = []

const option = ref({})

function loadData() {
  if (props.data.type === 'day') {
    stats = props.data.dayStats
  } else if (props.data.type === 'week') {
    stats = props.data.weekStats
  } else {
    stats = props.data.allStats
  }
  dislikes = stats.map((d) => {
    return d.dislikes
  })
  likes = stats.map((d) => {
    return d.likes
  })
  periode = stats.map((d, index) => {
    let end
    const date = d.date.toDate()
    if (index + 1 < stats.length) {
      end = stats[index + 1].date.toDate()
    } else end = stats[index].date.toDate()
    if (end - date <= 86400000) {
      if (props.data.type === 'week') {
        let newDate = date
        newDate.setDate(date.getDate() + 7)
        return `${stats[index].date.toDate().getDate()}-${newDate.getDate()}/${newDate.getMonth() + 1}`
      }
      return `${date.getDate()}/${date.getMonth() + 1}`
    }
    return `${date.getDate()}-${end.getDate()}/${end.getMonth() + 1}`
  })

  if (props.data.type === 'all') {
    likes.push(stats[0].likes)
    dislikes.push(stats[0].dislikes)
  } else {
    dislikes.pop()
    likes.pop()
    periode.pop()
  }
  if (props.data.type === 'all') {
    periode = ['All']
  }

  option.value = {
    title: {
      text: props.title,
      left: 'center'
    },
    tooltip: {
      trigger: 'item'
    },
    xAxis: {
      type: 'category',
      data: periode
    },
    yAxis: {
      type: 'value'
    },
    series: [
      {
        name: 'Likes',
        type: 'bar',
        stack: 'Total',
        data: likes,
        color: '#48982a'
      },
      {
        name: 'Dislikes',
        type: 'bar',
        stack: 'Total',
        data: dislikes.map((value) => value * -1),
        color: '#ea3423'
      }
    ]
  }
}

onBeforeUpdate(() => {
  loadData()
})
onBeforeMount(() => {
  loadData()
})
</script>

<style scoped>
.chart {
  height: 40vh;
}
</style>
