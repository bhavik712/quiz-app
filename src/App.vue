<template>
  <div>
    <div class="quiz-box">
      <div class="progress">
        <div
          class="bar"
          :style="{ width: `${(questionAnswered / questions.length) * 100}%` }"
        ></div>
        <div class="status">
          {{ questionAnswered }} Out of 3 Question answered
        </div>
      </div>
      <quiz-question
        :questionList="questions"
        :questionAnswered="questionAnswered"
        v-if="questionAnswered < questions.length"
        @selectedAnswer="OnAnswered"
      ></quiz-question>
      <quiz-result
        :resultList="results"
        :correctAnswers="correctAnswers"
        v-else
      ></quiz-result>

      <button class="reset-btn" @click="resetQuiz">Reset</button>
    </div>
  </div>
</template>

<script setup>
import QuizQuestion from "./components/questions.vue";
import QuizResult from "./components/result.vue";
import { useQuestion } from "./hooks/questionData";
import { useResult } from "./hooks/resultData";
import { ref } from "vue";

const { questions } = useQuestion();

const { results } = useResult();

let questionAnswered = ref(0);
let correctAnswers = ref(0);

const OnAnswered = (is_correct) => {
  if (is_correct) {
    correctAnswers.value++;
  }
  return questionAnswered.value++;
};
const resetQuiz = () => {
  questionAnswered.value = 0;
  correctAnswers.value = 0;
};
</script>

<style scoped></style>
