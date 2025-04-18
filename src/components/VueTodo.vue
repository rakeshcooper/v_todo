<template>
    <div>
        <h1>Todo</h1>
        <input type="text" name="inputTodo" id="inputTodo">
        <button>Add</button>
        <ul></ul>
        <button class="btn"  @click="countIncrement">count :{{ count }}</button>

    </div>
</template>

<script setup>
import { ref } from 'vue';

let count = ref(0)

function countIncrement(){
    count.value +=1

}
</script>

<style lang="scss" scoped>
    .btn{
        
    }
</style>