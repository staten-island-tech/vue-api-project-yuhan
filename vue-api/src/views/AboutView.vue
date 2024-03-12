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
