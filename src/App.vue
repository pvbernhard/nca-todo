<script setup>
import { ref } from "vue";

const tarefas = ref([]);

async function toggleTarefa(id) {
  const resultado = await fetch("http://localhost:8000/update/" + id)
    .then(response => response.json())
  
  if (resultado) {
    const tarefa = tarefas.value.find(tarefa => tarefa.id === id);
    tarefa.complete = !tarefa.complete;
  }
}

fetch("http://localhost:8000/")
    .then(response => response.json())
    .then(data => tarefas.value = data);
</script>

<template>
<div class="container">
  <header class="text-center text-light my-4">
    <h1 class="mb-4">✍️ Tarefas</h1>
    <form class="add text-center my-4">
      <label class="text-light">O que você quer fazer? 🤔</label>
      <input class="form-control m-auto my-4" type="text" placeholder="ex.: aprender vue" name="add" />
      <div class="text-center">
        <input type="submit" class="btn btn-light" value="Adicionar tarefa" />
      </div>
    </form>
  </header>

  <ul v-for="tarefa in tarefas" :key="tarefa.id" class="list-group todos mx-auto text-light delete">
    <li
      class="list-group-item d-flex justify-content-between align-items-center"
    >
      <div class="form-check">
        <input class="form-check-input" type="checkbox" :checked="tarefa.complete" :id="'check-' + tarefa.id" @click="toggleTarefa(tarefa.id)">
        <label class="form-check-label" :for="'check-' + tarefa.id" :class="{ 'tarefa-concluida': tarefa.complete }">
          {{ tarefa.title }}
        </label>
      </div>
      <div class="actions">
        <button class="btn btn-danger">Delete</button>
      </div>
    </li>
  </ul>
</div>
</template>

<style scoped>
.tarefa-concluida {
  text-decoration: line-through;
}
</style>
