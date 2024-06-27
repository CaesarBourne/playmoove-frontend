<template>
    <div>
      <form @submit.prevent="submitForm">
        <div>
          <label for="username">Username:</label>
          <input type="text" v-model="username" id="username" required>
        </div>
        <div>
          <label for="password">Password:</label>
          <input type="password" v-model="password" id="password" required>
        </div>
        <button type="submit">Login</button>
      </form>
    </div>
  </template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      username: '',
      password: ''
    }
  },
  methods: {
    async submitForm() {
      try {
        const response = await axios.post('http://localhost:8000/api/login', {
          username: this.username,
          password: this.password
        });
        console.log(response.data);
      } catch (error) {
        console.error(error);
      }
    }
  }
}
</script>