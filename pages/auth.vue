<template>
  <div class="container">
    <form @submit.prevent="handleLogin" method="post">
      <input type="text" v-model="dialCode" placeholder="Dial code">
      <input type="text" v-model="phone" placeholder="Phone">
      <input type="text" v-model="identity" placeholder="Identity">
      <button type="submit">Login</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dialCode: '',
      phone: '',
      identity: ''
    };
  },
  methods: {
    async handleLogin() {
      const BASE_URL = 'https://elkodaa.chd-staging.tech//api/c/auth/login';

      try
      {
        const response = await this.$axios.post(BASE_URL, {
          dialCode: this.dialCode,
          phone: this.phone,
          identity: this.identity
        });

        console.log('Authentication successful:', response.data);
      }
      catch (error)
      {
        console.error('Authentication error:', error.message);

      }
    }
  }
};
</script>

<style scoped>
@import '@/CSS/style.css';
</style>


