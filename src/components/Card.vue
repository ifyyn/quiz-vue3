
<script setup>
import { defineProps } from 'vue';
import { useRouter } from 'vue-router';

const router = useRouter()
const {quis} = defineProps(['quis'])

function goQuiz(){
  router.push({name: 'quis',params:{id:quis.id}})
}

</script>

<template>
    <div class="card-body">
         <div class="card" @click="goQuiz()">
           <img v-bind:src="quis.img" alt="">
           <h2>{{ quis.title }}</h2>
           
           <h3>{{ quis.questions.length }} Questions</h3>
         </div>
       </div>
 </template>

<style scoped>
    .card{
    width: 270px;
    border-radius: 5px;
    background-color: white;
    padding: 10px;
    margin: 10px;
    cursor: pointer;
  }
  .card img{
    width: 270px;
    height: 200px;
  }
  .card h2{
    font-size: 20px;
    font-weight: bold;
    color: #4ed492;
  }
</style>