<template>
  <transition name="fade">
    <div class="question-box">
      <div class="current-question">{{ getQuestion.q }}</div>
      <div
        class="answers"
        v-for="option in getQuestion.answers"
        :key="option.text"
      >
        <div class="answer" @click="emits('selectedAnswer', option.is_correct)">
          {{ option.text }}
        </div>
      </div>
    </div>
  </transition>
</template>

<script setup>
import { computed } from "vue";

const props = defineProps(["questionList", "questionAnswered"]);
const emits = defineEmits(["selectedAnswer"]);

const getQuestion = computed(() => props.questionList[props.questionAnswered]);
</script>
