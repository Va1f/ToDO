<template>
  <div id="app">
    <h1>To-Do List</h1>
    <AddTask />
    <TaskList />
  </div>
</template>

<script lang="ts" setup>
import AddTask from './components/AddTask.vue';
import TaskList from './components/TaskList.vue';
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 20px;
}
</style>
