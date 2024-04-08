<template>
  <div>
    <div class="container">
        <h1>Login</h1>
        <form @submit.prevent="login">
        <label for="email">Email</label>
        <input type="email" id="email" v-model="email" required>
        <label for="password">Password</label>
        <input type="password" id="password" v-model="password" required>
        <button type="submit">Login</button>
    </form>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      email: '',
      password: ''
    };
  },
  methods: {
    async authenticateUser()
    {
      try
      {
        const response = await axios.post('https:/elkodaa.chd-staging.tech/api/c/auth/login', this.credentials);
        return response.data; // This will return the data returned from the backend API
      }
      catch (error)
      {
        console.log("أول مشكلة")
        throw error; // Handle error appropriately (e.g., display error message)
      }
    },
    async login() {
      try
      {
        const response = await this.authenticateUser();
        // Handle successful authentication response here
      } catch (error)
      {
        // Handle error (e.g., display error message)
        alert("ثاني مشكلة")
        console.error('Authentication failed:', error);
      }
    }
  }
};
</script>

<style scoped>
@import '@/CSS/style.css';
</style>


