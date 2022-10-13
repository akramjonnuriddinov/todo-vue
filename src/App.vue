<template>
  <div class="w-full mt-5 h-auto container border bg-white rounded py-5 max-w-md mx-auto px-5">
    <h1 class="text-4xl font-semibold mb-4">{{ header }}</h1>
    <div class="flex justify-between items-center mb-4">
      <input class="mr-2 border p-2 w-full" v-model.trim="input_value" type="text" placeholder="Add Yout New ToDo">
      <button @click="addItem" class="px-3 bg-pink-500 rounded pb-1 text-white font-bold text-4xl flex items-center justify-center" type="button">+</button>
    </div>
    <ul>
      <li class="mb-2 last:mb-0 flex justify-between" v-for="item in items">
        <p class="bg-gray-200 rounded p-3 cursor-pointer w-full">{{ item.text }}</p>
        <button @click="deleteItem" class="rounded-tr rounded-br font-medium px-1 text-lg bg-pink-500 text-white" type="button">Delete</button>
      </li>
    </ul>
    <div class="flex justify-between items-center py-4">
      <p>You have {{ result }} pending tasks</p>
      <button @click="clearItems" class="rounded font-medium px-1 py-2 text-lg bg-pink-500 text-white" type="button">Clear All</button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const header = ref('Todo App');
const input_value = ref()
let result = ref(0)

const items = ref([
  // {id: 0, text: ''}
]);

function addItem() {
  if(input_value.value !== '') {
    items.value.push({id: items.value.length + 1, text: input_value.value})
    input_value.value = ''
  }
}


function deleteItem() { 
  items.value.pop()
}

</script>

<style>
body {
  background-color: rgb(80, 227, 238);
}
</style>