<template>
  <div v-if="destination">
    <section class="destination">
      <h1>{{ destination.name }}</h1>
      <GoBack />
      <div class="destination-details">
        <img :src="`/images/${destination.image}`" :alt="destination.name" />
        <p>{{ destination.description }}</p>
      </div>
    </section>
    <section class="experiences">
      <h2>Top Experiences in {{ destination.name }}</h2>
      <div class="cards">
        <router-link
          v-for="experience in destination.experiences"
          :key="experience.slug"
          :to="{
            name: 'experience.show',
            params: { experienceSlug: experience.slug },
          }"
        >
          <ExperienceCard :experience="experience" />
        </router-link>
      </div>
      <router-view />
    </section>
  </div>
</template>
<script>
import ExperienceCard from "@/components/ExperienceCard.vue";
import sourceData from "../data.json";
import GoBack from "@/components/GoBack.vue";

export default {
  components: {
    ExperienceCard,
    GoBack,
  },
  props: {
    id: { type: Number, required: true },
  },
  computed: {
    destinationId() {
      return parseInt(this.$route.params.id);
    },
    destination() {
      return sourceData.destinations.find(
        (destination) => destination.id == this.destinationId
      );
    },
  },
  // async created() {
  //   // using the watch method to fetch the destination data
  //   // this.$watch(
  //   //   () => this.$route.params,
  //   //   () => {
  //   //     this.fetchDestination();
  //   //   },
  //   //   { immediate: true }
  //   // );
  // },
  // methods: {
  //   async fetchDestination() {
  //     const respose = await fetch(
  //       `https://travel-dummy-api.netlify.app/${this.$route.params.slug}.json`
  //     );
  //     this.destination = await respose.json();
  //   },
  // },
};
</script>
