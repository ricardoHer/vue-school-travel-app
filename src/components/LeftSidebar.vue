<template>
  <ul>
    <li>
      <router-link to="/protected">Dashboard</router-link>
    </li>
    <li>
      <router-link to="/invoices">Invoices</router-link>
    </li>
  </ul>
</template>
<style scoped>
ul {
  background: white;
  padding: 10px;
  list-style: none;
  margin-right: 20px;
}
li {
  margin: 10px;
}
</style>
