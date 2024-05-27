<script setup>
import QuisContentVue from "@/components/QuisContent.vue";
import QuisHeaderVue from "@/components/QuisHeader.vue";
import QuisResult from "@/components/QuisResult.vue"
import { useRoute } from "vue-router";
import quiz from '../data/quiz.json'
import {ref, watch,computed} from 'vue'

const route = useRoute()
const quizId = parseInt(route.params.id)
const quis = quiz.find((q) => q.id === quizId)
console.log(quis)


const showResult = ref(false)
const numberOfCorrectAnswer = ref(0)
const currenQuestionIndex = ref(0)

const questionPage = computed(()=>{
    return `${currenQuestionIndex.value + 1} / ${quis.questions.length}`
})

const barPercentage = computed(()=>{
    return `${((currenQuestionIndex.value + 1) / quis.questions.length) * 100}%`
})

function onSelectOption(option){
    if(option.correct){
        numberOfCorrectAnswer.value++;
    }
    if(currenQuestionIndex.value === quis.questions.length - 1){
        showResult.value = true;
        return;
    }
    currenQuestionIndex.value++
}
// const questionPage = ref(
//     `${currenQuestionIndex.value + 1} / ${quis.questions.length}`
// )
   
// watch(()=> currenQuestionIndex.value,()=> {
//     questionPage.value = `${currenQuestionIndex.value + 1} / ${quis.questions.length}`
// })
  
</script>
<template>
    <QuisHeaderVue :questionPage="questionPage" :barPercentage="barPercentage"/>
   <QuisContentVue :question="quis.questions[currenQuestionIndex]" @selecOption="onSelectOption" v-if="!showResult"/>
  <QuisResult v-else :quisLength="quis.questions.length" :numberOfCorrectAnswer="numberOfCorrectAnswer"/>
</template>

<style scoped>
    
</style>
