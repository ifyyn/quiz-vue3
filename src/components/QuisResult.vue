<script setup>
    import {defineProps} from 'vue';
    import {RouterLink} from 'vue-router'
    const {quisLength, numberOfCorrectAnswer} = defineProps([
        'quisLength',
        'numberOfCorrectAnswer'
    ]);
</script>

<template>
    <section class="result">
        <p>Score:</p>
        <h1>{{ numberOfCorrectAnswer }}/{{ quisLength }}</h1>
        <RouterLink to="/">Go Back</RouterLink>
    </section>
</template>

<style scoped>
    .result{
        text-align: center;
        padding: 100px 0;
    }
    p{
        font-size: 25px;
        color: aliceblue;
    }
    h1{
        font-size:80px;
    }
</style>