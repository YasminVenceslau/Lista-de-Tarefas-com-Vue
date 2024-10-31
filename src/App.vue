<script setup>
  import {reactive} from 'vue';
  import Cabecalho from './components/Cabecalho.vue'
  import Formulario from './components/Formulario.vue'
  import ListaDetarefas from './components/ListaDetarefas.vue'
  
  const estado = reactive({
    filtro: 'todas',
    tarefaTemp: '',    
    tarefa: [
      {
        titulo: 'Estudar ESC6',
        finalizadas: false,
      },
      {
        titulo: 'Estudar Sass',
        finalizadas: false,
      },
      {
        titulo: 'Ir para casa',
        finalizadas: true,
      }
    
    ]
  })

  const getTarefasPendentes = () => {
    return estado.tarefa.filter(tarefa => !tarefa.finalizadas)
  }

  const getTarefasFinalizadas = () => {
    return estado.tarefa.filter(tarefa => tarefa.finalizadas)
  }

  const getTarefasFiltradas = () => {
    const { filtro }= estado;

    switch (filtro) {
      case 'Pendentes':
        return getTarefasPendentes();
      case 'finalizadas':
        return getTarefasFinalizadas()
      default:
        return estado.tarefa
    }
  }

  const CadastrarTarefa = () =>{
    
    const tarefaNova = {
      titulo: estado.tarefaTemp,
      finalizadas: false,
    }

    estado.tarefa.push(tarefaNova);
    estado.tarefaTemp = '';
  }
</script>

<template >
<div class="container "> 

  <Cabecalho :tarefas-pendentes="getTarefasPendentes().length" />
  <Formulario :trocar-filtro="evento => estado.filtro = evento.target.value" :tarefa-temp="estado.tarefaTemp" :edita-tarefa-temp="evento => estado.tarefaTemp = evento.target.value" :cadastrar-tarefa="CadastrarTarefa"/>
  <ListaDetarefas :tarefas="getTarefasFiltradas()"/>


</div>
</template>


