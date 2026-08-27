<template>
  <div class="min-h-screen">
    <Header class="z-50" />
    <main class="relative z-0">
      <slot />
    </main>
    <Footer class="mt-auto" />
  </div>
</template>

<script setup>
import Header from './Header.vue'
import Footer from './Footer.vue'
</script>

<style scoped>
</style>