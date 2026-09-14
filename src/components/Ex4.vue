<script setup>
import { ref } from 'vue'
const items = ref(['keyboard', 'mouse', 'iPhone', 'macbook', 'adapter'])

// TODO: Add Code Here
function deleteItem(item){
    let idx = -1
    for (const stuff of items.value){
        if (stuff.trim() === item.trim()){
            idx = items.value.indexOf(stuff)
        }
    }
    items.value.splice(idx, 1)
}

const chosenItem = ref("")

function addItem(){
    if (chosenItem.value.trim() !== ""){
        items.value.push(chosenItem.value)
        chosenItem.value = ""
    }
}

</script>

<template>

    <h2>Shopping Cart</h2>
    <!-- TODO: Add Code Here -->

    <ul v-for="item in items" v-bind:key="item">
        <li>{{ item }}
            <button v-on:click="deleteItem(item)">Delete!</button>
        </li>
    </ul>
    <input v-model="chosenItem" type="text">
    <button v-on:click="addItem(chosenItem)">Add!</button>
</template>
