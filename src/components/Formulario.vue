<script setup>
     const props = defineProps(['cadastrarTarefa', 'tarefaInicial', 'trocarFiltro', 'editaTarefaInicial'])
</script>
<template>
    <form @submit.prevent="props.cadastrarTarefa">
            <div class="row">
                <div class="col">
                    <input :value="props.tarefaInicial" required @change="props.editaTarefaInicial" type="text" placeholder="Digite aqui a descrição da tarefa" class="form-control">
                </div>
                <div class="col-md-2">
                    <button type="submit" class="btn btn-primary">Cadastrar Atividade</button>
                </div>
                <div class="col-md-2">
                    <select @change="props.trocarFiltro" class="form-select form-select-sm" aria-label="Small">
                        <option value="todas">Todas as tarefas</option>
                        <option value="pendentes">Pendentes</option>
                        <option value="finalizadas">Finalizadas</option>
                    </select>
                </div>
            </div>
        </form>
</template>