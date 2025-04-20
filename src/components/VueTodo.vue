<template>
    <div>
        <h1>Todo</h1>
        <input @input="getInputvalue" type="text" name="inputTodo" id="inputTodo">
        <button @click="addHandler">Add</button>
        <ul>
            <li :key="dat" v-for="dat in data">
                <span>{{ dat.todo }}</span>
                <span v-if="dat.isEdited"><input @input="updateInputvalue" type="text"><button @click="updateHandler(dat.ID)">update</button></span>
                <span><button @click="editHandler(dat.ID)">{{dat.isEdited ? "cancel" : "edit"}}</button></span>
                <span><button @click="deleteHandler(dat.ID)">delete</button></span>
                <span><button>{{dat.isChecked ? "undone" : "done"}}</button></span>
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
    setData = { todo: newData ,ID: cryptoId, isChecked: false, isEdited: false}
    console.log(setData);
    data.push(setData)
}


function getInputvalue(e){
    console.log(e.target.value);
    newData = e.target.value
}

function editHandler(ID){
    data.forEach((element, index) => {
        if (element.ID === ID) {
        data[index] = { ...element, isEdited: !element.isEdited }
        }
    });
}

function updateInputvalue(e){
    console.log(e.target.value);
    newData = e.target.value
}


function updateHandler(ID){
    data.forEach((element,index) => {
        if(element.ID == ID){
            data[index] = { ...element, todo: newData, isEdited: !element.isEdited }
        } 
    })
}

function deleteHandler(ID){
    data.forEach((element,index) => {
        data.splice(index, 1)
    })
}


</script>

<style lang="scss" scoped>
    button{
        cursor: pointer;
    }
</style>