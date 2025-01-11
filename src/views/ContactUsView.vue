<script setup lang="ts">
import ContactUsForm from "@/components/forms/ContactUsForm.vue";
</script>

<template>
  <div class="contact-us-wrapper">
    <ContactUsForm />
  </div>
</template>

<style>
.contact-us-wrapper {
  background-color: #0f1c0f;
  min-height: calc(100vh - var(--header-height));
}
</style>
