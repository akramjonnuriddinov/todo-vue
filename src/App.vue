<template>
  <div class="container w-full h-auto max-w-md px-5 py-5 mx-auto mt-5 bg-white border rounded">
    <h1 class="mb-4 text-4xl font-semibold">{{ header }}</h1>
    <div class="flex items-center justify-between mb-4">
      <input class="w-full p-2 mr-2 border" v-model.trim="input_value" type="text" placeholder="Add Yout New ToDo">
      <button @click="addItem" class="flex items-center justify-center px-3 pb-1 text-4xl font-bold text-white bg-pink-500 rounded" type="button">+</button>
    </div>
    <ul>
      <li class="flex justify-between mb-2 last:mb-0" v-for="item in items">
        <p class="w-full p-3 bg-gray-200 rounded cursor-pointer">{{ item.text }}</p>
        <button @click="deleteItem(index)" class="px-1 text-lg font-medium text-white bg-pink-500 rounded-tr rounded-br" type="button">Delete</button>
      </li>
    </ul>
    <div class="flex items-center justify-between py-4">
      <p>You have {{ result }} pending tasks</p>
      <button @click="clearItems" class="px-1 py-2 text-lg font-medium text-white bg-pink-500 rounded" type="button">Clear All</button>
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

function deleteItem(index) { 
  items.value.splice(index, 1)
}

</script>

<style>
body {
  background-color: rgb(80, 227, 238);
}
</style>