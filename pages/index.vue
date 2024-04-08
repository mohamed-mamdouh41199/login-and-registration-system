<template>
  <div>
    <div class="container">
        <h1>Welcome to My Website</h1>
        <button @click="goToLogin">Login</button>
        <button @click="goToRegister">Register</button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    goToLogin() {
      this.$router.push('/login');
    },
    goToRegister() {
      this.$router.push('/reg');
    }
  }
}
</script>

<style scoped>
@import '@/CSS/style.css';
</style>
