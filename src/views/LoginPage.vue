<template>
  <div class="login">
    <form class="form" @submit.prevent="login">
      <h1>Login</h1>
      <label for="email">Email:</label>
      <input
        class="input"
        type="email"
        id="email"
        v-model="username"
        required
      />
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
import { ref } from "vue";
import { useRouter, useRoute } from "vue-router";

export default {
  setup() {
    const username = ref("");
    const password = ref("");
    const router = useRouter();
    const route = useRoute();

    const login = () => {
      window.user = username.value;
      console.log("UserName: ", username.value);
      const redirectPath = route.query.redirect || "/protected";
      router.push(redirectPath);
    };
    return { username, password, login };
  },
};
</script>

<style scoped>
/* Add your custom styles here */
</style>
