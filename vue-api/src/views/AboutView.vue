<template>
  <div class="about">
    <h1>Chart</h1>
  </div>
  <div style="width: 800px;"><canvas id="acquisitions"></canvas></div>
</template>

<script setup>

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

(async function() {
  const data = [ 
    { year: 2010, count: 10 },
    { year: 2011, count: 20 },
    { year: 2012, count: 15 },
    { year: 2013, count: 25 },
    { year: 2014, count: 22 },
    { year: 2015, count: 30 },
    { year: 2016, count: 28 },
  ];

new Chart(
  document.getElementById('acquisitions'),
  {
    type: 'bar',
    data: {
      labels: data.map(row => row.year),
      datasets: [
        {
          label: 'Acquisitions by year',
          data: data.map(row => row.count)
        }
      ]
    }
  }
)})

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
