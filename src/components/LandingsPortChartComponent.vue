<template>
        <Bar :data="data" :options="options" />
</template>
  
  <script>
import {Chart as ChartJS,  Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale} from 'chart.js'
import { Bar } from 'vue-chartjs'
import NEP_cat_byport_2023_data from '@/data/landings/NEP_cat_byport_2023'

ChartJS.register(CategoryScale, LinearScale, BarElement, Title, Tooltip, Legend)

export default {
  name: 'App',
  components: {
    Bar
  },
  data() {
    return {
      data: {
        labels: NEP_cat_byport_2023_data.data.map(row => row.Name),
        datasets: [{ 
            data: NEP_cat_byport_2023_data.data.map(row => row.kg),
            backgroundColor: "#7BBC8C" 
            }]
      },
      options: {
        responsive: true,
        indexAxis: 'y',
        plugins: {legend: {display: false}},
        scales: {x:{title: {text:'Species landings 2023 (Kg)', display: true}}},
        maintainAspectRatio: false
      }
    }
  }
}
  </script>
  