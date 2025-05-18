<script > //using options API
export default {
  data() {
    return {
      name: "John Doe",
      status: "inactive",
      tasks: ["cleaning", "coding", "cooking", "going to class"],
      link: "https://www.aliexpress.com/"
    };
  },
  methods: {
    toggleStatus() {
      if(this.status === "active")
    {
      this.status = "pending";
    }
    else if(this.status === "pending")
    {
      this.status = "inactive";
    }
    else
    {
      this.status = 'active';
    }
    }
  }
}
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
  <!-- <a v-bind:href="link">Click Me</a > -->
   <a :href="link">Click Me!</a>

   <!-- <button v-on:click="toggleStatus">Change Status</button> -->
  <button @click="toggleStatus">Change Status</button>
</template>


