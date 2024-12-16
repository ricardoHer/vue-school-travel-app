<template>
  <TheNavigation />
  <div class="container">
    <!-- The :key value will force the Vue to reload the page, to have a fresh information -->
    <!-- :key="$route.path" -->
    <router-view v-slot="{ Component }">
      <transition name="slide" mode="out-in">
        <component :is="Component" :key="$route.path"></component>
      </transition>
    </router-view>
  </div>
</template>

<script>
import TheNavigation from "@/components/TheNavigation.vue";
export default {
  components: {
    TheNavigation,
  },
};
</script>
<style lang="css">
.slide-enter-active,
.slide-leave-active {
  transition: opacity 0.4s, transform 0.4s;
}
.slide-enter-from,
.slide-leave-to {
  opacity: 0;
  transform: translateX(-50%);
}

.moveUp-entter-active {
  animation: fadeIn 0.4s ease-in;
}

/* @keyframes fadeIn {
  0% {
    opaticy: 0;
  }
  50% {
    opaticy: 0.5;
  }
  100% {
    opaticy: 1;
  }
}

.moveUp-leave-active {
  animation: moveUp 0.3s ease-in;
}

@keyframes moveUp {
  0% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(-100%);
  }
} */
</style>
