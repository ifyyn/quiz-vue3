<script setup>
import {defineProps} from 'vue'

const {questionPage, barPercentage} = defineProps(['questionPage','barPercentage']);


</script>


<template>
    <header>
        <h2>Quetion {{ questionPage }}</h2>
        <div class="bar">
            <div class="bar-progres" :style="{width:barPercentage}"></div>
        </div>
    </header>
</template>

<style scoped>
    header{
        margin-top: 20px;
    }
    header h2{
        font-size: 30px;
        color: aliceblue;
    }
    .bar{
        width: 100%;
        height: 50px;
        border: 3px solid aliceblue;
    }
    .bar-progres{
        height: 100%;
        width: 0%;
        background-color: rgb(114, 212, 114);
    }
</style>