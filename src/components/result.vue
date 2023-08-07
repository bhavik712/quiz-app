<template>
   <div class="result-box">
        <div class="result"> You have given {{ correctAnswers }} answers correctly.</div>
        <div class="desc" v-for="(result,index) in resultList" v-show="index === correctAnswers">{{ result.desc }}</div>
    </div>
</template>

<script>
    export default {
        name:'Result',
        props:['resultList','correctAnswers']
        
    }
</script>

