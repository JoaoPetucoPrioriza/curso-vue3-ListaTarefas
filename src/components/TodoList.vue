<template>
  <v-text-field clearable label="Adicionar Tarefa" :rules="rules" v-model="taskStore.titleTaskCreating"
    @keyup.enter="taskStore.addTask">
  </v-text-field>

  <ListTasks />
</template>

<script setup>
import { onMounted } from 'vue';
import ListTasks from './ListTasks.vue'
import { useTaskStore } from '@/store/task';

const taskStore = useTaskStore();

const rules = [
  value => {
    if (!value || value.length >= 5) return true

    return 'Preencha o título com mais de 5 caracteres. '
  },
];

onMounted(() => {
  taskStore.getTasks();
});
</script>