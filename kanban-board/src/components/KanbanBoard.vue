<template>
  <v-container fluid>
    <v-row class="text-center">
      <v-col cols="4">
        <h2 class="text-h5 font-weight-bold">Skal laves</h2>
        <div class="drop-zone" 
          @drop="onDrop($event, 'todo')" 
          @dragenter.prevent
          @dragover.prevent
        >
          <item v-for="task in todoTasks" 
            :key="task.id" 
            :task="task" 
          />
        </div>
      </v-col>
      <v-col cols="4">
        <h2 class="text-h5 font-weight-bold">Igangværende</h2>
        <div class="drop-zone" 
          @drop="onDrop($event, 'inProgress')" 
          @dragenter.prevent @dragover.prevent
        >
          <item v-for="task in inProgressTasks" 
            :key="task.id" 
            :task="task" 
          />
        </div>
      </v-col>
      <v-col cols="4">
        <h2 class="text-h5 font-weight-bold">Afsluttet</h2>
        <div class="drop-zone" 
          @drop="onDrop($event, 'done')" 
          @dragenter.prevent 
          @dragover.prevent
        >
          <item v-for="task in doneTasks" 
            :key="task.id" 
            :task="task" 
          />
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup lang="ts">
import { ref } from 'vue';

// Data for dummy tasks that should be made draggable. Maybe move to seperate data.js and inject

const todoTasks = ref([
  { id: 1, title: 'Task 1', description: 'Description for Task 1', color: 'lightgreen' },
  { id: 2, title: 'Task 2', description: 'Description for Task 2', color: 'lightgreen' },
  { id: 3, title: 'Task 3', description: 'Description for Task 3', color: 'lightgreen' },
]);

const inProgressTasks = ref([
  { id: 4, title: 'Task 4', description: 'Description for Task 4', color: '#efbcb3' },
  { id: 5, title: 'Task 5', description: 'Description for Task 5', color: '#efbcb3' },
]);

const doneTasks = ref([
  { id: 6, title: 'Task 6', description: 'Description for Task 6', color: '#fbebbb' },
  { id: 7, title: 'Task 7', description: 'Description for Task 7', color: '#fbebbb' },
  { id: 8, title: 'Task 8', description: 'Description for Task 8', color: '#fbebbb' },
]);

const onDrop = (event, list) => {
  const taskId = event.dataTransfer.getData('taskId');
  const task = todoTasks.value.find(task => task.id.toString() === taskId)
            || inProgressTasks.value.find(task => task.id.toString() === taskId)
            || doneTasks.value.find(task => task.id.toString() === taskId);

  if (task) {
    // Remove the task from its original list
    const originalList = getListByTaskId(taskId);
    if (originalList) {
      originalList.splice(originalList.indexOf(task), 1);
    }

    // Determine the color based on the column
    let color = '';
    switch (list) {
      case 'todo':
        color = 'lightgreen';
        break;
      case 'inProgress':
        color = '#efbcb3';
        break;
      case 'done':
        color = '#fbebbb';
        break;
      default:
        break;
    }

    // Update the color
    task.color = color;

    // Add the task to other list
    switch (list) {
      case 'todo':
        todoTasks.value.push(task);
        break;
      case 'inProgress':
        inProgressTasks.value.push(task);
        break;
      case 'done':
        doneTasks.value.push(task);
        break;
      default:
        break;
    }
  }
};

// Helper function to find task.id of drag object
const getListByTaskId = (taskId) => {
  if (todoTasks.value.some(task => task.id.toString() === taskId)) {
    return todoTasks.value;
  } else if (inProgressTasks.value.some(task => task.id.toString() === taskId)) {
    return inProgressTasks.value;
  } else if (doneTasks.value.some(task => task.id.toString() === taskId)) {
    return doneTasks.value;
  } else {
    return null;
  }
};
</script>
