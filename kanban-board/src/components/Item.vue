<template>
    <v-card class="my-3" :style="{ backgroundColor: task.color }" draggable="true" @dragstart="startDrag">
      <v-card-title class="headline text-uppercase" style="color: black">{{ task.title }}</v-card-title>
      <v-card-text style="color: black">{{ task.description }}</v-card-text>
    </v-card>
  </template>
  
  <script setup lang="ts">
  import { defineProps } from 'vue';
  
  const props = defineProps({
    task: Object
  });
  
  const startDrag = (event) => {
    event.dataTransfer.setData('taskId', props.task.id.toString());
  };
  </script>
  