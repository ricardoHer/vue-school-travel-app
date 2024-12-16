<template>
  <div class="login">
    <form class="form" @submit.prevent="login">
      <h1>Login</h1>
      <label for="email">Email:</label>
      <input class="input" type="email" id="email" v-model="email" required />
      <label for="password">Password:</label>
      <input
        class="input"
        type="password"
        id="password"
        v-model="password"
        required
      />
      <button class="btn" type="submit">Login</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    login() {
      // Perform login logic here
      console.log("Logging in...");
      window.user = this.email;
      this.$router.push({ name: "protected" });
    },
  },
};
</script>

<style scoped>
/* Add your custom styles here */
</style>
