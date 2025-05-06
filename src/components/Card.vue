<script setup>
const emit = defineEmits(["turnAround", "statusChange"]);

</script>

<template>
  <div class="container">
    <div class="card">
      <div class="card-number">06</div>
      <div class="card-text">слово</div>
      <div class="card-action">Перевернуть</div>
    </div>
  </div>
</template>

<style scoped>
.container {
  border-radius: 16px;
  width: 250px;
  height: 376px;

  box-shadow: 0 0 16px 0 rgba(0, 0, 0, 0.1);
  background: #fff;

  display: flex;
  align-items: center;
  justify-content: center;

}

.card {
  border: 1px solid #cce8ff;
  border-radius: 12px;
  width: 212px;
  height: 320px;
  background: #fff;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.card-number {
  width: 16px;
  height: 16px;
  background-color: #fff;
  padding: 0 4px;

font-weight: 400;
font-size: 14px;
text-align: center;
color: #000;

}

.card-action {
  padding: 0 4px;
  width: 97px;
  height: 18px;
  background-color: #fff;
  text-transform: uppercase;

  text-align: center;

  font-weight: 700;
  font-size: 12px;
  line-height: 150%;
  letter-spacing: 0.12em;
  color: #222;
  align-self: center;
}

.card-text {
  font-weight: 400;
  font-size: 18px;
  text-align: center;
  color: #000;
}

</style>