<template>
  <!--header <container-->
  <div class="header">
    <div class="title">
      <h1>TO DO LIST</h1>
    </div>
    <hr />
    <form @submit.prevent="addTask" class="form">
      
        <label><h2>Title</h2></label>
        <input v-model="newTask.title" type="text" placeholder="Title">
      
      
        <label><h2>Details</h2></label>
        <textarea v-model="newTask.description" type="text" placeholder="Description"> </textarea>
        <button id="submit-btn" type="submit" >Add ToDo</button>
    </form>
  </div>
  <!-- body container -->
  <div class="todo-body">
    <ul>
      <li v-for="(task, index) in tasks" :key="index" class="list-item">
        <strong>{{ task.title }}</strong>: {{ task.description }}
        <button @click="removeTask(index)">x</button>
      </li>
    </ul>
  </div>
</template>

<script>
import { reactive } from 'vue';

export default{
  setup() {
    const state = reactive({
      tasks: [],
      newTask: {
        title: '',
        description: ''
      }
    });

    const addTask = () => {
      state.tasks.push({...state.newTask});
      state.newTask.title = '';
      state.newTask.description = '';
    };

    const removeTask = (index) => {
      state.tasks.splice(index, 1);
    };

    return {
      tasks: state.tasks,
      newTask: state.newTask,
      addTask,
      removeTask,
    };
  }
};
</script>

<style scoped>
/* styling the header part from here */
.header {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100vw;
  height: 100%;
}

.title {
  margin-top: 2rem;
  /* font-family:'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif; */
  font-size: 3rem;
  color: rgb(37, 15, 80);
}
hr {
  color: rgb(2, 1, 1);
  font-size: 2px;
  width: 100%;
}
.form {
  margin: 2rem 0 3rem 0;
  display: flex;
}
.form label{
  margin-right: 1rem;
}
.form input{
  margin-right: 1rem;
}

.form #submit-btn:hover {
 cursor: pointer;
}
.form textarea {
  border: none;
  border-radius: 0.7rem;
  resize: none;
  margin-right: 1rem;
  padding: 2rem 0 3rem 2rem;
}

/* styling the list body part from here */

.todo-body{
  height: 100%;
  box-sizing: border-box;
  width: 20rem;
}

.todo-body .list-item{
  background-color: rgb(0, 197, 246);
  height: 10rem;
}
</style>

