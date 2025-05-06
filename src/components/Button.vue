<script setup>

</script>

<template>
  <button class="button">
    <slot />
  </button>
</template>

<style scoped>
.button{
  width:335px;
  border: none;
  border-radius: 100px;
  padding: 14px;
  background: var(--color-bg-button);
  font-family: var(--font), sans-serif;
  font-size: 24px;
  font-weight: 400;
  color: var(--color-button);
  cursor: pointer;
}
.button:hover{
  background: var(--color-bg-button-hover);
}
</style>