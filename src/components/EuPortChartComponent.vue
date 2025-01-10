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
            data: NEP_cat_byport_2023_data.data.map(row => row.eu),
            backgroundColor: "#496CAD" 
            }]
      },
      options: {
        responsive: true,
        indexAxis: 'y',
        plugins: {legend: {display: false},
                  title: {
                    display:true,
                    text: 'Species income by port 2023'
                  }},
        scales: {x:{title: {text:'Euros (€)', display: true}}},
        maintainAspectRatio: false
      }
    }
  }
}
  </script>
  