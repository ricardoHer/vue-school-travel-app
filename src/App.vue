<template>
  <TheNavigation />
  <div class="container">
    <router-view
      v-slot="{ Component }"
      class="view left-sidebar"
      name="LeftSidebar"
    >
      <transition name="fade" mode="out-in">
        <component :is="Component" :key="$route.path"></component>
      </transition>
    </router-view>
    <!-- The :key value will force the Vue to reload the page, to have a fresh information -->
    <!-- :key="$route.path" -->
    <router-view v-slot="{ Component }" class="main-view">
      <transition name="fade" mode="out-in">
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
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.moveUp-entter-active {
  animation: fadeIn 0.4s ease-in;
}

.container {
  display: flex;
}

.left-sidebar {
  width: 20%;
}

.main-view {
  width: 100%;
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
