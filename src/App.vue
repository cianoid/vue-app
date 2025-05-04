<script setup>
import { ref } from 'vue';
const dateString = ref(new Date().toLocaleDateString());
</script>

<template>
  <div id="app">
    <h1>Vue basics</h1>
    <p>Current date: {{ dateString }}</p>
  </div>
</template>

<style scoped>
</style>
