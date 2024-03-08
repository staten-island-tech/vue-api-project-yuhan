<template>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
</template>

<script setup>

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
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
