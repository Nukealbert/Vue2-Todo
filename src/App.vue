<template>
  <div id="app">
    <h1>Vue 2 To-Do List</h1>
    <div>
      <input v-model="newTask" @keyup.enter="addTask" placeholder="Add a new task">
      <ul>
        <li v-for="(task, index) in tasks" :key="index">
          <span :class="{ 'completed': task.completed }">{{ task.title }}</span>
          <button @click="toggleTask(index)" v-if="task.completed">Mark as uncompleted</button>
          <button @click="toggleTask(index)" v-else>Mark as completed</button>
          <button @click="removeTask(index)" >Remove</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: [],
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== '') {
        this.tasks.push({ title: this.newTask, completed: false });
        this.newTask = '';
      }
    },
    toggleTask(index) {
      this.tasks[index].completed = !this.tasks[index].completed;
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: 'Arial', sans-serif;
  text-align: center;
  margin-top: 50px;
}

h1 {
  color: #333;
}

div {
  max-width: 400px;
  margin: 0 auto;
}

input {
  width: 100%;
  padding: 10px;
  box-sizing: border-box;
  margin-bottom: 10px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #f9f9f9;
  border: 1px solid #ddd;
  margin-bottom: 5px;
  padding: 10px;
}

.completed {
  text-decoration: line-through;
  color: #999;
}

button {
  background-color: #dc3545;
  color: white;
  border: none;
  padding: 8px 12px;
  cursor: pointer;
}

button:hover {
  background-color: #c82333;
}
</style>

