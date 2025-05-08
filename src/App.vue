<script setup>
import {computed, ref} from "vue";
import Button from "./components/Button.vue";
import Score from "./components/Score.vue";
import Card from "./components/Card.vue";

function getTurned() {
}

let score = ref(100);
let cards = ref([
  {
    word: "word",
    translation: "слово",
    state: "closed",
    status: "pending",
  },
  {
    word: "elephant",
    translation: "слон",
    state: "opened",
    status: "pending",
  },
  {
    word: "car",
    translation: "автомобиль",
    state: "opened",
    status: "success",
  },
  {
    word: "cablecar",
    translation: "канатная дорога",
    state: "opened",
    status: "fail",
  },
])

let cardsData = computed(() => {
  let data = {};
  for (let i = 0; i < cards.value.length; i++) {
    data[i] = cards.value[i];
    data[i].number = i > 9 ? `${i+1}` : `0${i+1}`;
  }
  return data;
})
</script>

<template>
  <div id="app" class="main">
    <div class="menu">
      <div class="title">Запомни слово</div>
      <Score :score="score"/>
    </div>

    <Button class="button-game-start">
      Начать игру
    </Button>
  </div>

  <div class="cards">
    <Card v-for="item in cardsData" :key="item.word" v-bind="item" @flipped="getTurned" />
  </div>

</template>

<style scoped>
.main {
  background-color: var(--color-bg);
}
.cards{
  display: flex;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 1rem;
}

.menu {
  height: 121px;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;

}

.title {
  font-weight: 700;
  font-size: 16px;
  line-height: 150%;
  letter-spacing: 0.12em;
  color: #222;
  text-transform: uppercase;
}
</style>
