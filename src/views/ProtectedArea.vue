<template>
  <div>
    <h1>Greetings, {{ userName }}</h1>
    <button class="btn" @click="logout">Logout</button>&nbsp;
    <button class="btn" @click="goToInvoices">Go to invoices</button>&nbsp;
  </div>
</template>
<script>
export default {
  data() {
    return {
      userName: window.user,
    };
  },
  methods: {
    logout() {
      window.user = null;
      this.$router.push({ name: "home" });
    },
    goToInvoices() {
      this.$router.push({ name: "invoices" });
    },
  },
};
</script>
