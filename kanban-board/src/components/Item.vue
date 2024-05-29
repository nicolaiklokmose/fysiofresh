<template>
    <v-card class="my-3" :style="{ backgroundColor: color }">
      <v-card-title class="headline" style="color: black">{{ title }}</v-card-title>
      <v-card-text style="color: black">{{ description }}</v-card-text>
    </v-card>
  </template>
  
  <script setup lang="ts">
    import { defineProps } from 'vue';
  
    const props = defineProps({
      id: Number,
      title: String,
      description: String,
      color: String,
    });
  </script>
  