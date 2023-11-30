<script setup>
import { ref, onMounted } from 'vue'

const tasks = ref([{ text: 'apple', checked: false }, { text: 'ananas', checked: true }]);
const input = ref(null); // Define the input variable

onMounted(() => {
  input.value.focus()
})

function addTask() {
  tasks.value.push({ text: input.value, checked: false }); // Use input.value to get the input value
  input.value = ''; // Clear the input field after adding the task
}

function deleteTask() {
  // TODO
}

</script>

<template>
  <main class="p-2 flex flex-col space-y-2 mx-auto max-w-2xl">
    <h1 class="text-xl">
      Todo List
    </h1>
    <form @submit.prevent="addTask" class="flex flex-col space-y-2">
      <label for="">Tâche à ajouter</label>
      <input v-model="input" type="text" placeholder="truc à faire" class="block border-black border-2">
      <input type="submit" class="font-white-500 bg-blue-500 block">
    </form>
    <h2 class="text-lg">Liste des tâches</h2>
    <ul class="divide-y divide-slate-200">
      <li v-for="task in tasks" :key="index" class="flex justify-around">
        <input type="checkbox" v-model="task.checked">{{ task.text }}
        <button @click="deleteTask" class="text-red-500">DELETE</button>
      </li>
    </ul>
  </main>
</template>