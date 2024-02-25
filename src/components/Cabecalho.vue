<script setup>
     const props = defineProps(['tarefasPendentes'])
</script>
<template>
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
        <h1>Minhas Tarefas</h1>
        <p>
            Você possui {{ props.tarefasPendentes }} tarefas pendentes
        </p>
    </header>

    
            <!-- <button type="button" class="btn btn-primary position-relative">
                Inbox
                <span class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-danger">
                    99+
                    <span class="visually-hidden">unread messages</span>
                </span>
            </button> -->
</template>

