<template>
  <v-container class="fill-height" style="color: black">
    <v-row>
      <!-- Skal laves -->
      <v-col cols="4">
        <h2 class="text-h5 font-weight-bold">Skal laves</h2>
        <item v-for="task in todoTasks" :key="task.id" :id="task.id" :title="task.title" :description="task.description" color="#884939" />
      </v-col>
      
      <!-- Igangværende -->
      <v-col cols="4">
        <h2 class="text-h5 font-weight-bold">Igangværende</h2>
        <item v-for="task in inProgressTasks" :key="task.id" :id="task.id" :title="task.title" :description="task.description" color="#efbcb3" />
      </v-col>
      
      <!-- Afsluttet -->
      <v-col cols="4">
        <h2 class="text-h5 font-weight-bold">Afsluttet</h2>
        <item v-for="task in doneTasks" :key="task.id" :id="task.id" :title="task.title" :description="task.description" color="#fbebbc" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup lang="ts">
  import { ref } from 'vue';

  const todoTasks = ref([
    { id: 1, title: 'Task 1', description: 'Description for Task 1' },
    { id: 2, title: 'Task 2', description: 'Description for Task 2' },
    { id: 3, title: 'Task 3', description: 'Description for Task 3' },
  ]);

  const inProgressTasks = ref([
    { id: 4, title: 'Task 4', description: 'Description for Task 4' },
    { id: 5, title: 'Task 5', description: 'Description for Task 5' },
  ]);

  const doneTasks = ref([
    { id: 6, title: 'Task 6', description: 'Description for Task 6' },
    { id: 7, title: 'Task 7', description: 'Description for Task 7' },
    { id: 8, title: 'Task 8', description: 'Description for Task 8' },
  ]);
</script>
