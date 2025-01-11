<script setup lang="ts">
import { RouterLink } from "vue-router";
</script>

<template>
  <header>
    <div class="wrapper">
      <RouterLink to="/" class="home-title">Home</RouterLink>

      <nav>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/contact-us">Contact Us</RouterLink>
      </nav>
    </div>
  </header>
</template>

<style scoped>
header {
  height: var(--header-height);
  padding: 0 32px;
  width: 100%;
  background: #222222;
  position: sticky;
  top: 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.home-title {
  text-transform: uppercase;
  font-weight: 700;
}

.home-title:hover {
  background: transparent;
}

.wrapper {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

@media (max-width: 1024px) {
  header {
    width: 100%;
  }
}
</style>
