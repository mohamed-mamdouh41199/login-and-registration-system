<template>
  <div class="container">
    <h1>Registration</h1>
    <form @submit.prevent="register">
      <div>
        <label for="firstName">First Name</label>
        <input type="text" id="firstName" v-model="firstName" required>
      </div>
      <div>
        <label for="lastName">Last Name</label>
        <input type="text" id="lastName" v-model="lastName" required>
      </div>
      <div>
        <label for="email">Email</label>
        <input type="email" id="email" v-model="email" required>
      </div>
      <div>
        <label for="password">Password</label>
        <input type="password" id="password" v-model="password" required>
      </div>
      <div>
        <label for="confirmPassword">Confirm Password</label>
        <input type="password" id="confirmPassword" v-model="confirmPassword" required>
      </div>
      <button type="submit">Register</button>
    </form>
  </div>
</template>
<script>
import axios from "axios";

export default {
  data() {
    return {
      userData: {
        firstName: "",
        lastName: "",
        name: "",
        email: "",
        password: ""
      }
    };
  },
  methods: {
    async registerUser()
    {
      try
      {
        const response = await axios.post('https://elkodaa.chd-staging.tech//api/c/auth/login', this.userData);
        return response.data;
      }
      catch (error)
      {
        throw error;
      }
    },
    async register()
    {
      try
      {
        const response = await this.registerUser();
        console.log('Registration successful:', response);
        // Handle successful registration response here
      } catch (error)
      {
        console.error('Registration failed:', error);
        // Handle error (e.g., display error message)
      }
    }
  }
};
</script>


<style scoped>
</style>
