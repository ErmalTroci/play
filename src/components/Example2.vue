<script setup lang="ts">
import {onMounted, ref} from "vue";
import autoAnimate from "@formkit/auto-animate";

let todos = ref([
  {id: 1, body: 'Go to gym!', completed: false},
  {id: 2, body: 'Pray!', completed: true},
  {id: 3, body: 'Drink coffe', completed: false},
  {id: 4, body: 'Play tennis', completed: false},
]);

let newTodo = ref('');
function addTodo(){
  todos.value.push({
    id: todos.length + 1,
    body: newTodo.value,
    completed: false
  });

  newTodo.value = '';
}

function shuffleTodos() {
  todos.value.sort(() => 0.5 - Math.random());
}
</script>

<template>
  <section ref="container">
    <h1>Todos</h1>
    <div class="mt-4" v-auto-animate>
      <div v-for="todo in todos" :key="todo.id" class="flex justify-between gap-x-6 bg-gray-200 mb-4 px-3 py-2 rounded">
        <p class="text-black">{{todo.body}}</p>
          <input type="checkbox" :checked="todo.completed">
      </div>
      <div>
        <form @submit.prevent="addTodo">
          <textarea name="" id="" cols="30" rows="4" class="border" v-model="newTodo" required></textarea>
          <div>
            <button class="bg-primary">Submit</button>
            <button class="bg-primary" type="button" @click="shuffleTodos">Shuffle</button>
          </div>
        </form>
      </div>
    </div>
  </section>

</template>