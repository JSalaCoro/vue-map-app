

<template>
        <Bar :data="data" :options="options" />
</template>
  
  <script>
 import {Chart as ChartJS,  Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale} from 'chart.js'
import { Bar } from 'vue-chartjs'
import NEP_cat_byport_2023_json_data from '@/data/NEP_cat_byport_2023_json'

ChartJS.register(CategoryScale, LinearScale, BarElement, Title, Tooltip, Legend)

export default {
  name: 'App',
  components: {
    Bar
  },
  data() {
    return {
      data: {
        labels: NEP_cat_byport_2023_json_data.data.map(row => row.Name),
        datasets: [{ 
            data: NEP_cat_byport_2023_json_data.data.map(row => row.kg),
            }]
      },
      options: {
        responsive: true,
        indexAxis: 'y',
        plugins: {legend: {display: false}},
        scales: {x:{title: {text:'Species landings (Kg)', display: true}}},
        maintainAspectRatio: false
      }
    }
  }
}
  </script>
  