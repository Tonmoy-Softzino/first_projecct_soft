<template>
    <form @submit.prevent="addTask">
        <label>Title</label>
        <input v-model="newTask.title" type="text" placeholder="Title">
    </form>
</template>

<script setup>
    import { reactive } from 'vue'

    const state = reactive({
      tasks: [],
      newTask: {
        id: '',
        title: ''
      }
    });

    const addTask = () => {
      state.tasks.push({...state.newTask});
      state.newTask.title = '';
      state.newTask.id = state.tasks.length + 1;
    };
</script>