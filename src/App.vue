<script setup>
import { ref } from 'vue'

let id = 0
const newItem = ref('')
const items = ref([])

function addItem() {
  items.value.push({ id: id++, task: newItem.value })
  newItem.value = ''
}

function removeItem(item) {
  items.value = items.value.filter((t) => t !== item)
}
</script>

<template>
    <input class="myinput" v-model="newItem" placeholder="Enter new item"> &nbsp;
    <button class="mybutton" @click="addItem">Add</button>
  
  <ul>
    <li v-for="item in items" :key="item.id">
      {{ item.task }}
      <button class="mybutton"  @click="removeItem(item)">Delete</button>
    </li>
  </ul>
</template>

<style>
body, html {
  height: 100%;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

.myinput {
  width: 200px;
  padding: 5px;
}

.mybutton {
  background-color: lightblue;
  padding: 3px;
  margin: 3px;
}
</style>