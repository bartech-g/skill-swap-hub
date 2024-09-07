<template>
  <nav class="bg-blue-600 p-4">
    <div class="container mx-auto flex justify-between items-center">
      <!-- Logo or Brand Name -->
      <router-link to="/" class="text-white text-lg font-semibold"> Skill Swapp </router-link>

      <!-- Navigation Links -->
      <ul class="flex space-x-6">
        <!-- Modal Toggle Link -->
        <li>
          <span
            role="link"
            @click="showModal = true"
            class="cursor-pointer text-white hover:text-blue-300"
          >
            Show Modal
          </span>
        </li>

        <!-- Router Link Example -->
        <li>
          <router-link to="/about" class="text-white hover:text-blue-300" role="link">
            About
          </router-link>
        </li>
      </ul>
    </div>
  </nav>
  <AppModal v-model="showModal">
    <h2>Modal Title</h2>
    <FirebaseLogin />
  </AppModal>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import AppModal from '@/components/Base/AppModal.vue'
import FirebaseLogin from '../Auth/FirebaseLogin.vue'
// Reactive state for modal visibility
const showModal = ref<boolean>(false)
</script>

<style scoped></style>
