<template>
  <div id="nav">
    <router-link id="logo" :to="{ name: 'home' }"
      >VueSchool TRavel App</router-link
    >
    <router-link
      v-for="destination in destinations"
      :key="destination.id"
      :to="{
        name: 'destination.show',
        params: { id: destination.id, slug: destination.slug },
      }"
    >
      {{ destination.name }}
    </router-link>
    <router-link :to="{ name: 'protected' }">Protected</router-link>
  </div>
</template>
<script>
import sourceData from "@/data.json";
export default {
  data() {
    return {
      destinations: sourceData.destinations,
    };
  },
};
</script>
