<template>
  <transition name="fade">
    <div class="question-box">
      <div class="current-question">{{ getQuestion.q }}</div>
      <div
        class="answers"
        v-for="option in getQuestion.answers"
        :key="option.text"
      >
        <div class="answer" @click="$emit('selectedAnswer', option.is_correct)">
          {{ option.text }}
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: "Question",
  props: ["questionList", "questionAnswered"],
  emits: ["selectedAnswer"],

  computed: {
    getQuestion() {
      return this.questionList[this.questionAnswered];
    },
  },
};
</script>
