<script setup>//using Composition API
import { onMounted, ref } from 'vue';

//"state"
const name = ref("John doe");
const status = ref("active");
const tasks = ref(["Task One", "Task Two", "Task Three"]);
const newTask = ref("");
//functions


const toggleStatus = () => {
  if(status.value === "active")
    status.value = "pending";
  else if(status.value === "pending")
    status.value = "inactive";
  else
    status.value = 'active';
};

const addTask = () => {
  if(newTask.value.trim() !== "")
  {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
}

const deleteTask = (index) => {
  console.log("index:" + index)
  tasks.value.splice(index, 1);
}

onMounted(async () => {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/todos");
    const data = await response.json();
    tasks.value = data.map((task) => task.title);
  } catch (error) {
    console.log("Error fetching!");
    console.log(error);
  }
})

</script>
//render
<template>
  <h1>Hello {{name}}</h1>

  <p v-if="status === 'active'">User is Active</p>
  <p v-else-if="status === 'pending'">User is Pending</p>
  <p v-else>User is Inactive</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask">
    <button type="submit">Submit</button>
  </form>

  <h3>Tasks</h3>
  <ul v-for="(task, index) in tasks" :key="task">
    <li>
      <span>
        {{task}}
      </span>
       <button @click="deleteTask(index)">X</button>
    </li>
  </ul>
  <br>
  <!-- <button v-on:click="toggleStatus">Change Status</button> -->
  <button @click="toggleStatus">Change Status</button>
</template>


