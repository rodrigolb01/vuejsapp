<script >
export default {
  data() {
    return {
      name: "John Doe",
      status: "pendin"
    };
  }
}
</script>

<template>
  <h1>Hello {{name}}</h1>
  <p v-if="status === 'active'">User is Active</p>
  <p v-else-if="status === 'pending'">User is Pending</p>
  <p v-else>User is Inactive</p>
</template>


