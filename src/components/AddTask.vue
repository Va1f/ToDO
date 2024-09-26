<template>
  <div class="add-task">
    <input v-model="taskText" placeholder="Введите новую задачу" @keyup.enter="addTask" />
    <button @click="addTask">Добавить</button>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';
import { useTaskStore } from '../stores/taskStore';

const taskText = ref('');
const taskStore = useTaskStore();

const addTask = () => {
  if (taskText.value.trim()) {
    taskStore.addTask(taskText.value);
    taskText.value = '';
  }
};
</script>

<style scoped>
.add-task {
  display: flex;
  gap: 10px;
}
</style>
