<template>
    <v-card class="my-3" :style="{ backgroundColor: task.color }" draggable="true" @dragstart="startDrag">
<<<<<<< HEAD
      <v-card-title class="headline text-uppercase" style="color: black">{{ task.title }}</v-card-title>
      <v-card-text style="color: black">{{ task.description }}</v-card-text>
=======
      <v-card-title class="headline text-uppercase" style="color: #00796b">{{ task.title }}</v-card-title>
      <v-card-text style="color: #004d40">{{ task.description }}</v-card-text>
>>>>>>> test-nbk
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
<<<<<<< HEAD
=======
  
  <style>
  .v-card {
    border-radius: 10px;
    box-shadow: 0px 2px 6px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease-in-out;
  }
  
  .v-card:hover {
    transform: scale(1.05);
  }
  </style>
>>>>>>> test-nbk
  dddsdsdsadsadgit a