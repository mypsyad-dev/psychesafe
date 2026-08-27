<template>
  <router-view v-slot="{ Component }">
    <AppLayout>
      <component :is="Component" />
    </AppLayout>
  </router-view>
</template>

<script setup>
import AppLayout from '@/components/AppLayout.vue'
</script>

<style scoped>
</style>