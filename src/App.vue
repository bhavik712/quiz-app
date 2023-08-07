<template>
  <div>
    <div class="quiz-box">
      <div class="progress">
        <div class="bar" :style="{width: `${( questionAnswered / questions.length) * 100}%`}"></div>
        <div class="status"> {{ questionAnswered }} Out of 3 Question answered</div>
      </div>
        <question :questionList = "questions"  :questionAnswered = "questionAnswered" v-if="questionAnswered < questions.length" @selectedAnswer="OnAnswered"></question>
        <result :resultList="results" :correctAnswers="correctAnswers" v-else></result>

      <button class="reset-btn" @click="resetQuiz">Reset</button>
    </div>
  </div>
</template>

<script>
import Question from './components/questions.vue';
import Result from './components/result.vue';

export default {
  name:'App',
  components:{
    Question,
    Result
  },
  data(){
    return{
      questions: [
        {
          q: 'What is 2 + 2?', 
          answers: [
            {
              text: '4',
              is_correct: true
            },
            {
              text: '3',
              is_correct: false 
            },
            {
              text: 'Fish',
              is_correct: false 
            },
            {
              text: '5',
              is_correct: false 
            }
          ] 
        },
        { 
          q: 'How many letters are in the word "Banana"?', 
          answers: [
            {
              text: '5',
              is_correct: false
            },
            {
              text: '7',
              is_correct: false 
            },
            {
              text: '6',
              is_correct: true 
            },
            {
              text: '12',
              is_correct: false 
            }
          ] 
        },
        { 
          q: 'Find the missing letter: C_ke', 
          answers: [
            {
              text: 'e',
              is_correct: false
            },
            {
              text: 'a',
              is_correct: true 
            },
            {
              text: 'i',
              is_correct: false 
            },            
            {
              text: 't',
              is_correct: false
            }
            ] 
        },
    ],
    results: [
      {
        desc: 'Do not worry Go through the quiz Again'
      },
      {
        desc: 'Good Work! Practise Makes man perfect'
      },
      {
        desc: 'Nice try! You are almost there!'
      },
      {
        desc:'My Dear chmapion'
      }
      
    ],
    questionAnswered:0,
    correctAnswers:0
}
    },
  methods:{
    OnAnswered(is_correct){
      if(is_correct){
        this.correctAnswers++;
      }
      return this.questionAnswered++;
    },
    resetQuiz(){
      this.questionAnswered = 0;
      this.correctAnswers = 0;
    }
  }
}

</script>

<style scoped>

</style>




