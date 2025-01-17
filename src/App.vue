<script setup>
import { ref } from 'vue'

let id = 0
const newItem = ref('')
const items = ref([])

function addItem() {
  items.value.push({ id: id++, text: newItem.value })
  newItem.value = ''
}

function removeItem(item) {
  items.value = items.value.filter((t) => t !== item)
}
</script>

<template>
    <input v-model="newItem" placeholder="Enter new item"> &nbsp;
    <button @click="addItem">Add</button>
  
  <ul>
    <li v-for="item in items" :key="item.id">
      {{ item.text }}
      <button @click="removeItem(item)">Delete</button>
    </li>
  </ul>
</template>