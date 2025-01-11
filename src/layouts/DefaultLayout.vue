<script setup lang="ts">
import AppHeader from "@/components/common/AppHeader.vue";
</script>

<template>
  <div class="wrapper">
    <AppHeader />
    <main class="main-wrapper">
      <slot />
    </main>
  </div>
</template>

<style scoped>
.wrapper {
  min-height: 100vh;
}
.main-wrapper {
  min-height: calc(100vh - 60px);
}
</style>
