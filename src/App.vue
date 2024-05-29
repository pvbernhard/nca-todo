<script setup>

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

  <ul class="list-group todos mx-auto text-light delete">
    <li
      class="list-group-item d-flex justify-content-between align-items-center"
    >
      <div class="form-check">
        <input class="form-check-input" type="checkbox" value="" id="check-1">
        <label class="form-check-label" for="check-1">
          Tarefa #1
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

</style>
