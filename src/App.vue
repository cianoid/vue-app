<script setup>
import {computed, onMounted, ref} from "vue";
import Button from "./components/Button.vue";
import Score from "./components/Score.vue";
import Card from "./components/Card.vue";

function getTurned() {
}

let score = ref(100);
let cards = ref();
let error = ref();
let httpStatus = ref();
const API = "http://localhost:8080/api/random-words"
const errorMap = new Map([
  [1004, "Указанный город не найден"]
]);

async function loadCards() {
  const res = await fetch(API)
  cards.value = await res.json();
  httpStatus.value = res.status;

  if (httpStatus.value !== 200) {
    if (!cards.value) {
      error.value = {
        httpStatus: httpStatus.value,
        errorCode: 1000000,
        errorText: "Неизвестная ошибка",
      };
    } else {
      error.value = {
        httpStatus: httpStatus.value,
        errorCode: cards.value.error.code,
        errorText: errorMap.has(cards.value.error.code) ? errorMap.get(cards.value.error.code) : cards.value.error.message,
      };
    }
  } else {
    error.value = {};

    for (let i = 0; i < cards.value.length; i++) {
      cards.value[i].number = i > 9 ? `${i + 1}` : `0${i + 1}`;
      cards.value[i].state = "closed";
      cards.value[i].status = "pending";
    }
  }
}

onMounted(() => {
  loadCards();
});
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

  <div v-if="cards" class="cards">
    <Card v-for="item in cards" :key="item.word" v-bind="item" @flipped="getTurned"/>
  </div>

</template>

<style scoped>
.main {
  background-color: var(--color-bg);
}

.cards {
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
