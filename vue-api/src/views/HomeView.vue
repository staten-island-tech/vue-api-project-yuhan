<script setup>
import { ref, onMounted } from 'vue';

const abc = ref("");
async function getData(){
  try {
    let res = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json");
    let data = await res.json();
    // let deds = await res.leading_cause
    // console.log(deds)
    console.log(data)
  } catch (e) {
    console.error(e);
  }
}
  onMounted(() => {
  getData()
})



</script>

<template>

  </template>
