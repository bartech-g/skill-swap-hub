<template>
  <nav>
    <ul>
      <li><span role="link" @click="showModal = true">show modal</span></li>
      <li><router-link to="/about" role="link">about</router-link></li>
    </ul>
  </nav>
  <Modal v-model="showModal">
    <h2>Modal Title</h2>
    <Login />
  </Modal>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Modal from '@/components/Base/Modal.vue'
import Login from '../Auth/Login.vue'
// Reactive state for modal visibility
const showModal = ref<boolean>(false)
</script>

<style scoped></style>
