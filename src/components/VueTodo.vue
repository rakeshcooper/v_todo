<template>
    <div>
        <h1>Todo</h1>
        <input @input="getInputvalue" type="text" name="inputTodo" id="inputTodo">
        <button @click="addHandler">Add</button>
        <ul>
            <li :key="dat" v-for="dat in data">
                <span>{{ dat.todo }}</span>
                <span><input type="text"><button>update</button></span>
                <span><button>edit</button></span>
                <span><button>delete</button></span>
                <span><button>done</button></span>
            </li>
        </ul>

    </div>
</template>

<script setup>
import { ref, reactive } from 'vue';
let cryptoId 
let newData 
let data = reactive([])
let setData


function addHandler(){
    cryptoId = crypto.randomUUID()
    setData = { todo: newData ,ID: cryptoId, isChecked: false, isDeleted: false}
    console.log(setData);
    data.push(setData)
}


function getInputvalue(e){
    console.log(e.target.value);
    newData = e.target.value
}


</script>

<style lang="scss" scoped>
    button{
        cursor: pointer;
    }
</style>