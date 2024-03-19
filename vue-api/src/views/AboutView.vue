<template>
 <BarChart>  </BarChart> Chart couldn't be loaded.
</template>

<script>
import BarChart from '../components/BarChart.vue';

import { ref, onMounted } from 'vue';
const abc = ref("");
async function getData(){
  let res = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json");
  let data = await res.json();
  abc.value = data.results;

}

onMounted(() => {
  getData()
})

</script>
<style>

</style>
