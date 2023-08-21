<template>
  <div class="result-box">
    <div class="result">
      You have given {{ props.correctAnswers }} answers correctly.
    </div>
    <div
      class="desc"
      v-for="(result, index) in props.resultList"
      v-show="index === props.correctAnswers"
    >
      {{ result.desc }}
    </div>
  </div>
</template>

<script setup>
const props = defineProps(["resultList", "correctAnswers"]);
</script>
