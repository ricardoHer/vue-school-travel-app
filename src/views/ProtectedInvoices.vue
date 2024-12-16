<template>
  <div>
    <h1>Invoices</h1>
    <p>
      Here you can find all your invoices. <br />
      <router-link to="/protected">Back to protected area</router-link>
    </p>
  </div>
</template>
<script>
import { onBeforeRouteLeave } from "vue-router";

export default {
  setup() {
    onBeforeRouteLeave(() => {
      const answer = window.confirm(
        "Are you sure you want to leave? You have unsaved changes!"
      );

      if (!answer) {
        return false;
      }
    });
  },
};
</script>
