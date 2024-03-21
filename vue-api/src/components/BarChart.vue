<template>
  <Bar
  id="my-chart-id"
  :options="chartOptions"
  :data="chartData"
  />
</template>

<script>
import { Bar} from "vue-chartjs";
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale, } from 'chart.js'


ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

const BarChart = {
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
export default BarChart
</script>