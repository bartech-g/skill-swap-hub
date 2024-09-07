<template>
  <AppNavigation />
  <RouterView />
</template>

<script setup lang="ts">
import { RouterView } from 'vue-router'
import AppNavigation from './components/Base/AppNavigation.vue'
</script>
