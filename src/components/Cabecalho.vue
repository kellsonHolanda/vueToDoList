<script setup>
const props = defineProps(['tarefasPendentes']);
</script>
<template>
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
        <h1>Minhas Tarefas</h1>
        <button type="button" class="btn btn-primary position-relative col-3 mx-auto btn-sm" style="--bs-btn-padding-y: .25rem; --bs-btn-padding-x: .5rem; --bs-btn-font-size: .75rem;" >
            <div v-if="props.tarefasPendentes > 0">
                <span>Você possui tarefas pendentes</span>
                <span class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-danger">
                    {{ props.tarefasPendentes }}
                </span>
            </div>
            <div v-else>
                <span>Nenhuma tarefa pendente</span>
                <span class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-danger">
                    {{ props.tarefasPendentes }}
                </span>
            </div>
        </button>
        
    </header>
</template>

