<template>
 <BarChart />
</template>

<script>

import { ref, onMounted } from 'vue';

const abc = ref("");
async function getData(){
  let res = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json");
  let data = await res.json();
  abc.value = data.results;
  console.log(data)
}

onMounted(() => {
  getData()
})

import BarChart from '../components/BarChart.vue'

export default {
  name: 'App',
  components: { BarChart }
}


</script>
<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
