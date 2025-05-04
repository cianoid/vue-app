<script setup>
let curDate = new Date();
let dateString = curDate.toLocaleDateString();
</script>

<template>
  <div id="app">
    <h1>Vue basics</h1>
    <p>Current date: {{ dateString }}</p>
  </div>
</template>

<style scoped>
</style>
