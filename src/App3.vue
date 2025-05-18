//using Composition API
// no need to export
// need to reference state by value
// use of ref()
//no need for the keyword this

<script setup>
import { ref } from 'vue';

  const name = ref("John doe");
  const status = ref("active");
  const tasks = ref(["Task One", "Task Two", "Task Three"]);

  const toggleStatus = () => {
  if(status.value === "active")
    status.value = "pending";
  else if(status.value === "pending")
    status.value = "inactive";
  else
    status.value = 'active';
  };
</script>

<template>
  <h1>Hello {{name}}</h1>

  <p v-if="status === 'active'">User is Active</p>
  <p v-else-if="status === 'pending'">User is Pending</p>
  <p v-else>User is Inactive</p>

  <h3>Tasks</h3>
  <ul v-for="task in tasks" :key="task">
    <h1>{{task}}</h1>
  </ul>

  <br>
   <!-- <button v-on:click="toggleStatus">Change Status</button> -->
  <button @click="toggleStatus">Change Status</button>
</template>


