<template>
  <v-app class="app">
    <Header />
    <v-main>
      <v-container fluid>
        <KanbanBoard />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import Header from './components/Header.vue';
import KanbanBoard from './components/KanbanBoard.vue';

export default {
  components: {
    Header,
    KanbanBoard
  }
}
</script>

<style>
.app {
  background-color: #f9f9f9;
  color: #333;
  font-family: 'Arial', sans-serif;
}
</style>
