<template>
  <ul class="task-list">
    <li v-for="task in tasks" :key="task.id" :class="{ completed: task.completed }">
      <input type="checkbox" :checked="task.completed" @change="toggleTaskCompletion(task.id)" />
      <span @dblclick="editMode(task)">{{ task.text }}</span>
      <button @click="removeTask(task.id)">Удалить</button>
      <input v-if="task.isEditing" v-model="task.text" @keyup.enter="stopEditing(task)" @blur="stopEditing(task)" />
    </li>
  </ul>
</template>

<script lang="ts" setup>
import { computed } from 'vue';
import { useTaskStore } from '../stores/taskStore';

const taskStore = useTaskStore();
const tasks = computed(() => taskStore.tasks);

const toggleTaskCompletion = (id: number) => {
  taskStore.toggleTaskCompletion(id);
};

const removeTask = (id: number) => {
  taskStore.removeTask(id);
};

const editMode = (task: any) => {
  task.isEditing = true;
};

const stopEditing = (task: any) => {
  task.isEditing = false;
  taskStore.editTask(task.id, task.text);
};
</script>

<style scoped>
.task-list li {
  display: flex;
  align-items: center;
  gap: 10px;
}

.completed span {
  text-decoration: line-through;
}
</style>
