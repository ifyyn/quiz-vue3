<script setup>
import {defineProps} from 'vue';

const emit = defineEmits(['selecOption'])
const {question} = defineProps(['question'])

function emitSelected(option){
    emit('selecOption',option)
}
</script>

<template>
    <section id="options-container">
        <h1 class="option-title">{{ question.text }}</h1>
        <div class="option" v-for="option in question.answers" :key="option.id" @click="emitSelected(option)">
            <p class="option-label">{{ option.label}}.</p>
            <div class="option-value">{{ option.text }}</div>
        </div>
    </section>
</template>
<style scoped>
    #options-container{
        margin-top: 30px;
    }
    .option-title{
        color: aliceblue;
        font-weight: bold;
    }
    .option{
        display: flex;
        align-items: center;
        color: black;
        font-weight: bold;
        cursor: pointer;
    }
    .option-label{
        width: 40px;
        height: 40px;
        background-color: aliceblue;
        display: flex;
        align-items: center;
        justify-content: center;
        
    }
    .option-value{
        width: 100%;
        height: 40px;
        background-color: #a0a0a0;
        display: flex;
        align-items: center;
        padding: 0 10px;
    }
    .option:hover .option-label{
        color: aqua;
    }
</style>