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
            label: 'Kg',
            data: NEP_cat_yearly_data.data.map(row => row.kg),
            backgroundColor: "#7BBC8C",
            borderColor: "#7BBC8C",
            yAxisID: 'y'          
            },
            {
            label: 'Eu',
            data: NEP_cat_yearly_data.data.map(row => row.eu),
            backgroundColor: "#496CAD",
            borderColor: "#496CAD",
            yAxisID: 'y1'
            }
          ]
      },
      options: {
        responsive: true,
        indexAxis: 'x',
        plugins: {legend: {display: true, position:'bottom'},
                  title: {
                    text:'Species landings evolution (Catalunya)',
                    display:true
                  }},
        scales: {
          y:{
            display: true,
            title: {text:'Kg', display: true}},
          y1: {
            display: true,
            title: {text:'Eu', display:true},
            position: 'right'
          }},
        maintainAspectRatio: false
        }
      }
    }
  }

  </script>
  