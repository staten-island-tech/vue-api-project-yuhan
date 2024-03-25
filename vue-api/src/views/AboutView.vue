<script setup>
import { ref, onMounted } from 'vue';
import Chart from '@/components/BarChart.vue';

const abc = [];//data from api
let years = []; //Array all year values
const loaded = ref(false); //loaded or not (to wait for api values)

async function getData(year){
  try {
    let res = await fetch(`
    https://data.cityofnewyork.us/resource/jb7j-dtam.json?$query=SELECT%0A%20%20%60year%60%2C%0A%20%20%60leading_cause%60%2C%0A%20%20%60sex%60%2C%0A%20%20%60race_ethnicity%60%2C%0A%20%20%60deaths%60%2C%0A%20%20%60death_rate%60%2C%0A%20%20%60age_adjusted_death_rate%60%0AWHERE%20caseless_one_of(%60year%60%2C%20%22${year}%22)`);
    let data = await res.json();
    return data
  } catch (e) {
    console.error(e);
  }
}

async function chart(){
for(let i = 0; i < years.length; i++){
  let yearfiltered = await getData(years[i])
  console.log(yearfiltered);
  let deathtotal = 0;
   for(let i = 0; i < yearfiltered.length; i++) {
  deathtotal += Number(yearfiltered[i].year) //years was a string;
}
console.log(deathtotal);
abc.push(deathtotal);
}
console.log(abc);
loaded.value = true;
}
  onMounted(async() => {
    loaded.value = false;
    const fetchYears = await fetch( //To get all the years
    "https://data.cityofnewyork.us/resource/jb7j-dtam.json?$query=SELECT%20%60year%60%20GROUP%20BY%20%60year%60%20ORDER%20BY%20%60year%60%20DESC%20NULL%20FIRST"
  );
  years = await fetchYears.json();
  years = years.map((yr) => yr.year);
  years = years.reverse();
  console.log(years);
  chart(); 
});

</script>

<template>
  <div class="big">
 <Chart v-if ="loaded" :data="abc" :labels="years"/> 
      <h1 v-else>wait ........</h1>
    </div>
  </template>