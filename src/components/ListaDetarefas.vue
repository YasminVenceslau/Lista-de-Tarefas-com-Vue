<script setup >
const props = defineProps(['tarefas']);
</script>

<template>
    <ul class="list-group mt-4 ">
        <li class="list-group-item list-group-item-info" v-for="tarefa in  tarefas">
            <input @change="evento => tarefa.finalizadas = evento.target.checked"  :checked="tarefa.finalizadas" :id="tarefa.titulo" type="checkbox" >
            <label :class="{done: tarefa.finalizadas }" class="ms-3 " :for="tarefa.titulo">
            {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
</template>

<style scoped>

.done{
transition: 1s ease;
  text-decoration: line-through;
}
</style>