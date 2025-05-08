<script setup>
import {computed, ref} from "vue";
import IconFail from "../icons/icon.fail.vue";
import IconSuccess from "../icons/icon.success.vue";

const {number = "00", word = "-", translation = "-", state = "closed", status = "pending"} = defineProps({
  number: String,
  word: String,
  translation: String,
  state: {
    type: String,
    default: "closed",
    validator(value) {
      return value === "closed" || value === "opened"
    },
  },
  status: {
    type: String,
    default: "pending",
    validator(value) {
      return value === "pending" || value === "success" || value === "fail"
    },
  }
});

const emit = defineEmits(["flipped", "statusChange"]);

const flipped = ref(false);

function turnCard() {
  flipped.value = !flipped.value;
  emit("flipped", flipped.value);
};

let isOpened = computed(() => state === 'opened');
let isSuccess = computed(() => status === 'success');
let isFail = computed(() => status === 'fail');
let isPending = computed(() => status === 'pending');
</script>

<template>
  <div class="container">
    <div class="card">
      <div class="card-top">
        <div class="card-number">{{ number }}</div>

        <div v-show="isOpened && isSuccess" class="card-result">
          <IconSuccess/>
        </div>
        <div v-show="isOpened && isFail" class="card-result">
          <IconFail/>
        </div>
      </div>

      <div v-if="isOpened" class="card-word">{{ word }}</div>
      <div v-else class="card-word">{{ translation }}</div>

      <div v-show="!isOpened && isPending" class="card-action" @click="turnCard()">Перевернуть</div>
      <div v-show="isOpened && (isSuccess || isFail)" class="card-action">Завершено</div>
      <div v-show="isOpened && isPending" class="card-action">
        <IconFail/>
        <IconSuccess/>
      </div>

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

.card-top {
  display: flex;
  align-items: center;
  gap: 50px;
}

.card-number {
  width: 16px;
  height: 36px;
  background-color: #fff;
  padding: 0 6px;
  font-weight: 400;
  font-size: 14px;
  text-align: center;
  color: #000;
  position: relative;
  top: -8px;
  left: 10px;
}

.card-result {
  width: 36px;
  height: 36px;
  background-color: #fff;
  padding: 0 6px;
  position: relative;
  top: -18px;
}

.card-action {
  padding: 0 6px;
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
  cursor: pointer;

  position: relative;
  bottom: -9px;

  display: flex;
  align-items: center;


}

.card-word {
  font-weight: 400;
  font-size: 18px;
  text-align: center;
  color: #000;
}

</style>