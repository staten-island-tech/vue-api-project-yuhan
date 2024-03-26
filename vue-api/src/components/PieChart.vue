<script>
import { Pie} from "vue-chartjs";
import { Chart as ChartJS, Tooltip, Legend, ArcElement,} from 'chart.js'


ChartJS.register(Tooltip, Legend, ArcElement,)

export default  {
    name: 'PieChart',
    components: { Pie }, 
    props: {
    data: Array,
    labels: Array,
  },
    data(){
        return{
            chartData: {
                labels: this.labels,
                datasets: [ 
                    {
                        label: 'Number Of Deaths',
                        backgroundColor: ['#ADD8E6', '#FF7F7F', '#90EE90', '#CBC3E3', '#Fed8b1', '#7F00FF', '#0000ff', '#3c1414'],
                        data: this.data
                    }
                ]
            },
            chartOptions: {
                responsive: true,
                maintainAspectRatio: false
            }
        }
    }
}

</script>
<template>
     <Pie
  id="my-chart-id"
  :options="chartOptions"
  :data="chartData"
  />
</template>