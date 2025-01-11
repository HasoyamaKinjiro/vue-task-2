<script setup lang="ts">
import { defineAsyncComponent } from "vue";

const TeamSection = defineAsyncComponent(() => import('@/components/pages/about/TeamSection.vue'));
</script>

<template>
  <main class="about">
    <section class="intro">
      <h1>About Us</h1>
      <p>
        Welcome to our about page! Lorem ipsum dolor sit amet, consectetur adipiscing elit.
        Our mission is to provide the best services to our customers.
      </p>
    </section>

    <section class="team">
      <h2>Meet Our Team</h2>
      <TeamSection />
    </section>
  </main>
</template>

<style scoped>
.about {
  font-family: Arial, sans-serif;
  padding: 2rem;
}

.intro {
  background: var(--green-bg-1);
  padding: 2rem;
  border-radius: 8px;
  margin-bottom: 2rem;
  text-align: center;
}

.intro h1 {
  font-size: 2rem;
  margin-bottom: 1rem;
}

.team {
  background: var(--green-bg-1);
  padding: 2rem;
  border-radius: 8px;
  margin-top: 2rem;
}

.team h2 {
  text-align: center;
  margin-bottom: 1rem;
}
</style>
