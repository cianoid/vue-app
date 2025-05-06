<script setup>
import IconScore from "../icons/icon.score.vue";
const props = defineProps({ score: { type: Number, default: 100 } });

</script>

<template>
<div class="container">
  {{props.score}} <IconScore/>
</div>
</template>

<style scoped>
.container{
  border-radius: 36px;
  padding: 12px 24px;
  width: 62px;
  height: 24px;
  box-shadow: 0 0 4px 0 rgba(0, 0, 0, 0.15);
  background: #cce8ff;

font-weight: 700;
font-size: 16px;
line-height: 150%;
text-align: center;
color: #008bfe;

  gap: 10px;

    display: flex;
  align-items: center;
  justify-content: center;

}
</style>