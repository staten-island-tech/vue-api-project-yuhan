<script>
import { Pie} from "vue-chartjs";
import { Chart as ChartJS, Tooltip, Legend, ArcElement,} from 'chart.js'


ChartJS.register(Tooltip, Legend, ArcElement,)

export default  {
    name: 'PieChart',
    components: { Pie }, 
    props: {
  
  },
    data(){
        return{
            chartData: {
                labels: this.labels,
                datasets: [ 
                    {
                        label: 'Number Of Deaths',
                        backgroundColor: '#ADD8E6',
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