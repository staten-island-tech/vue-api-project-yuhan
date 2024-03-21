<template>
  <Bar
  id="my-chart-id"
  :options="chartOptions"
  :data="chartData"
  />
</template>

<script>
import { Bar} from "vue-chartjs";
import { Chart as ChartJS, Title, Tooltip, Legend, CategoryScale, LinearScale, } from 'chart.js'


ChartJS.register(Bar, Title, Tooltip, Legend, CategoryScale, LinearScale)

export default  {
    name: 'BarChart',
    components: { Bar }, 
    data(){
        return{
            chartData: {
                labels: ['a', 'b', 'c'],
                datasets: [ {
                data: [1, 2, 3]}]
            },
            chartOptions: {
                responsive: true
            }
        }
    }
}

</script>