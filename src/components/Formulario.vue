<script setup>
  const props = defineProps(['cadastrarTarefa', 'tarefaTemp', 'trocarFiltro', 'editaTarefaTemp']);
</script>

<template>
  <form @submit.prevent="cadastrarTarefa">
    <div class="row">
      <div class="col">
        <input
          :value="tarefaTemp"
          @input="editaTarefaTemp"
          required
          type="text"
          placeholder="Digite aqui a descrição da tarefa"
          class="form-control"
        />
      </div>

      <div class="col-md-2">
        <button type="submit" class="btn btn-outline-info">Cadastrar</button>
      </div>

      <div class="col-md-2">
      <select @change="trocarFiltro" class="form-control">
          <option value="todas">Todas as tarefas</option>
          <option value="Pendentes">Tarefas Pendentes</option>
          <option value="finalizadas">Tarefas finalizadas</option>
        </select> 
      </div>
    </div>
  </form>
</template>
