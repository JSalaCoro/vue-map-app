<template>
        <Line :data="data" :options="options" />
</template>
  
  <script>
import {Chart as ChartJS,  Title, Tooltip, Legend, PointElement, LineElement, CategoryScale, LinearScale} from 'chart.js'
import { Line } from 'vue-chartjs'
import NEP_cat_yearly_data from '@/data/landings/NEP_cat_yearly'

ChartJS.register(CategoryScale, LinearScale, PointElement, LineElement, Title, Tooltip, Legend)

export default {
  name: 'App',
  components: {
    Line
  },
  data() {
    return {
      data: {
        labels: NEP_cat_yearly_data.data.map(row => row.year),
        datasets: [{ 
            data: NEP_cat_yearly_data.data.map(row => row.kg),
            backgroundColor: "#7BBC8C",
            borderColor: "#7BBC8C"           
            }]
      },
      options: {
        responsive: true,
        indexAxis: 'x',
        plugins: {legend: {display: false}},
        scales: {y:{title: {text:'Species landings (Kg)', display: true}}}
      }
    }
  }
}
  </script>
  