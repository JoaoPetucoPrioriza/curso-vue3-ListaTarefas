<template>
  <v-row justify="center">
    <v-dialog 
    v-model="taskStore.showDialogTaskFields" 
    persistent 
    min-width="400"
    max-width="600"
    >
      <v-card>
        <v-card-title class="text-h5">
          Editar Tarefa
        </v-card-title>
        <v-card-text>

            <v-text-field
            v-model="props.task.title"
            clearable 
            label="Título"
            ></v-text-field>

            <v-text-field 
            v-model="props.task.description"
            clearable 
            label="Descrição"
            ></v-text-field>
        </v-card-text
        >
        <v-card-actions>
          <v-spacer></v-spacer>

          <v-btn 
          color="primary-darken-1" 
          variant="elevated" 
          @click="taskStore.updateTask()"
          >
            Editar
          </v-btn>

        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script setup>
import { defineProps } from 'vue';
import { useTaskStore } from '@/store/task';

const taskStore = useTaskStore();
const props = defineProps({
    task: Object
})
</script>