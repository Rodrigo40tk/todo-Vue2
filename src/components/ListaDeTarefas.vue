<script setup>
const props = defineProps(['tarefas']);
</script>

<template>
    <div class="mt-4">
        <ul v-if="props.tarefas.length > 0" class="list-group">
            <li class="list-group-item" v-for="tarefa in props.tarefas" :key="tarefa.titulo">
                <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                    :id="tarefa.titulo" type="checkbox">
                <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
                    {{ tarefa.titulo }}
                </label>
            </li>
        </ul>
        <p v-else class="mt-3 text-muted">Não existem tarefas pendentes.</p>
    </div>
</template>


<style scoped>
.done {
    text-decoration: line-through;
}
</style>
