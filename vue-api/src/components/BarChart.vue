<template>
  <Bar
  id="my-chart-id"
  :options="chartOptions"
  :data="chartData"
  />
</template>

<script>
import { Bar,} from "vue-chartjs";
import { Chart as ChartJS, Title, Tooltip, Legend, CategoryScale, LinearScale, } from 'chart.js'

ChartJS.register(Bar, Title, Tooltip, Legend, CategoryScale, LinearScale)


const BarChart = {
    name: 'BarChart',
    components: { Bar }, 
    data(){
        return{
            chartData: {
                labels: ['January', 'February', 'March'],
                datasets: [ {
                data: [40, 20, 12]}]
            },
            chartOptions: {
                responsive: true
            }
        }
    }
}
export default BarChart
</script>