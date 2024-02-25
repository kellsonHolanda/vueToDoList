<script setup>
const props = defineProps(['tarefasFiltradas']);

</script>
<template>
    <div v-if="props.tarefasFiltradas.length > 0">
        <ul class="list-group mt-4">
            <li class="list-group-item" v-for="tarefa in props.tarefasFiltradas">
                <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                    :id="tarefa.titulo" type="checkbox">
                <label :class="{ done: tarefa.finalizada === true }" class="ms-3">{{ tarefa.titulo }}</label>
            </li>
        </ul>
    </div>
    <div v-else>
        <span class="ms-3">Você não possui tarefas com esse filtro </span>
    </div>
</template> 
<style scoped>
.done {
    text-decoration: line-through;
}
</style>