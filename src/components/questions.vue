<template>
    <transition-group name="fade">
        <div class="question-box" v-for=" (question,qi) in questionList" :key="question.q" v-show="qi == questionAnswered">
            <div class="current-question">{{ question.q }}</div>
            <div class="answers" v-for="(option,oi) in question.answers" :key="option.text">
                <div class="answer" @click="$emit('selectedAnswer', option.is_correct )">{{ option.text }}</div>
            </div>
        </div>
    </transition-group>
</template>

<script>
    export default {
        name:'Question',
        props:['questionList','questionAnswered'],
        emits: ['selectedAnswer']
    }
</script>

