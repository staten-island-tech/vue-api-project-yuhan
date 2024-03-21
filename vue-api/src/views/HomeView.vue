<script setup>
import { ref, onMounted } from 'vue';

const abc = ref("");
async function getData(){
  let res = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json");
  let data = await res.json();
  let deds = data.leading_cause
  console.log(deds)
}
  onMounted(() => {
  getData()
})



</script>

<template>

  </template>
