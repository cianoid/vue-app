<script setup>
import Button from "./components/Button.vue";
import Score from "./components/Score.vue";
// import Card from "./components/Card.vue";
</script>

<template>
  <div id="app" class="main">
    <div class="menu">
      <div class="title">Запомни слово</div>
      <Score />
    </div>


    <Button class="button-game-start">
      Начать игру
    </Button>
  </div>

<Card />

</template>

<style scoped>
.main {
  background-color: var(--color-bg);
}
.menu{
  height:121px;
  width:100%;
  display: flex;
  align-items: center;
  justify-content: center;

}
.title{
font-weight: 700;
font-size: 16px;
line-height: 150%;
letter-spacing: 0.12em;
color: #222;
  text-transform: uppercase;
}
</style>
