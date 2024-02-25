<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';

import Formulario from './components/Formulario.vue'
import ListaDeTarefas from './components/ListaDeTarefas.vue'
// const imagem = "https://getbootstrap.com/docs/5.3/assets/img/vite.svg";
const estado = reactive({
    filtro: 'todas',
    tarefaInicial: '',
    tarefa: [
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
    switch (filtro) {
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
        <Cabecalho :tarefas-pendentes="getTarefasPendentes().length" />
        <Formulario :cadastrar-tarefa="cadastrarTarefa" :tarefa-inicial="estado.tarefaInicial"
            :trocar-filtro="evento => estado.filtro = evento.target.value"
            :edita-tarefa-inicial="evento => estado.tarefaInicial = evento.target.value" />
        <ListaDeTarefas :tarefas-filtradas="getTarefasFiltradas()" />


    </div>


    <h1>Olá</h1>
</template>


