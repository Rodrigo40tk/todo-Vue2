<script setup>
import {reactive} from 'vue';

const estado = reactive({
  filtro:'todas',
  tarefas:[
    {
      titulo:'Estudar ES6',
      finalizada: false,
    },
    {
      titulo: 'Estudar SAAS',
      finalizada: false,
    },
    {
      titulo: 'Ir para a academia',
      finalizada: true,
    }
  ]
})

const getTarefasPendentes = () => {
  return estado.tarefas.filter(tarefa =>! tarefa.finalizada)
 
}
</script>

<template>
<div class="container">
  <header class="p-5 mb-4 mt-4 bg-light rounded-3">
    <h1>Minhas Tarefas</h1>
    <p>
      Você possui {{getTarefasPendentes().length}} tarefas pendentes
    </p>
  </header>
  <form>
  <div class="row">
    <div class="col">
      <input type="text" placeholder="Digite a descrição da tarefa" class="form-control">
    </div>
    <div class="col-md-2">
      <button type="submit" class="btn btn-primary">Cadastrar</button>
    </div>
    <div class="col-md-2">
      <select @change="evento => estado.filtro = evento.target.value" class="form-control">
        <option value="todas">Todas tarefas</option>
        <option value="pendentes">Todas pendentes</option>
        <option value="finalizadas">Todas finalizadas</option>
      </select>
    </div>
  </div>
</form>
<ul class="list-group mt-4">
  <li class="list-group-item" v-for="tarefa in estado.tarefas">
    <input :checked="tarefa.finalizada" :id="tarefa.titulo" type="checkbox">
    <label :class="{done: tarefa.finalizada ===true}" class="ms-3" :for="tarefa.titulo">
      {{tarefa.titulo}}
    </label>
  </li>
</ul>
</div>
</template>

<style scoped>

.done{
  text-decoration: line-through;
}
</style>
