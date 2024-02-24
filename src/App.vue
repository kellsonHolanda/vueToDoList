<script setup>
import { reactive } from 'vue';
// const imagem = "https://getbootstrap.com/docs/5.3/assets/img/vite.svg";
const estado = reactive({
    filtro: 'todas',
    tarefaInicial: '',
    tarefa:[
    {
        titulo: 'Estudar ES6',
        finalizada: false,
    },
    {
        titulo: 'Estudar SASS',
        finalizada: false,
    },
    {
        titulo: 'Estudar JavaScript',
        finalizada: true,
    }
]
})

const getTarefasPendentes = () => {
    return estado.tarefa.filter(tarefa => tarefa.finalizada === false)
}
const getTarefasFinalizadas = () => {
    return estado.tarefa.filter(tarefa => tarefa.finalizada === true)
}

const getTarefasFiltradas = () => {
    const filtro = estado.filtro;
    switch(filtro){
        case 'pendentes':
            return getTarefasPendentes();
        case 'finalizadas':
            return getTarefasFinalizadas();
        default:
            return estado.tarefa;
    }
}

const cadastrarTarefa = () => {
    const tarefaNova = {
        titulo: estado.tarefaInicial,
        finalizada: false,
    }
    estado.tarefa.push(tarefaNova);
    estado.tarefaInicial = '';
}


</script>

<template>
    <div class="container">
        <header class="p-5 mb-4 mt-4 bg-light rounded-3">
            <h1>Minhas Tarefas</h1>
            <p>
                Você possui {{ getTarefasPendentes().length }} tarefas pendentes
            </p>
            <!-- <button type="button" class="btn btn-primary position-relative">
                Inbox
                <span class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-danger">
                    99+
                    <span class="visually-hidden">unread messages</span>
                </span>
            </button> -->
        </header>
        <form @submit.prevent="cadastrarTarefa">
            <div class="row">
                <div class="col">
                    <input :value="estado.tarefaInicial" required @change="evento => estado.tarefaInicial = evento.target.value" type="text" placeholder="Digite aqui a descrição da tarefa" class="form-control">
                </div>
                <div class="col-md-2">
                    <button type="submit" class="btn btn-primary">Cadastrar Atividade</button>
                </div>
                <div class="col-md-2">
                    <select @change="evento => estado.filtro = evento.target.value" class="form-select form-select-sm" aria-label="Small">
                        <option value="todas">Todas as tarefas</option>
                        <option value="pendentes">Pendentes</option>
                        <option value="finalizadas">Finalizadas</option>
                    </select>
                </div>
            </div>
        </form>
        
        <ul class="list-group mt-4">
            <li class="list-group-item" v-for="tarefa in getTarefasFiltradas()">
                <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada" :id="tarefa.titulo" type="checkbox">
                <label :class="{ done: tarefa.finalizada === true}" class="ms-3">{{tarefa.titulo}}</label>

            </li>
        </ul>
    </div>


    <h1>Olá</h1>
</template>

<style scoped>
.done {
    text-decoration: line-through;
}
</style>
