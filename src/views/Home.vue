<script setup>
import dataQuiz from '../data/quiz.json';
import { ref,watch } from 'vue';
import Card from '../components/Card.vue'

const quiz = ref(dataQuiz)
const search = ref("")

watch(search,()=>{
  quiz.value = dataQuiz.filter((quis)=>{
    return quis.title.toLowerCase().includes(search.value.toLowerCase())
  })
})

</script>

<template>
    <header>
      <h1 class="title">QUIZ.<span>Vue</span></h1>
      <input v-model="search" type="text" placeholder="search quiz">
    </header>
    <section id="card-container">
      <Card v-for="quis in quiz" :key="quis.id" v-bind:quis="quis"/>
    </section>
</template>


<style scoped>
  header{
    display: flex;
    margin-top: 20px;
    gap: 30px;
    align-items: center;
  }
  .title{
    font-size: 30px;
    color: aliceblue;
  }
  .title span{
    color: #4ed492;
    font-size: 32px;
  }
  input{
    padding: 9px;
  }
  #card-container{
    display: flex;
    flex-wrap: wrap;
    margin-top: 20px;
  }
</style>