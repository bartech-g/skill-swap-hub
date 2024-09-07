<template>
  <div v-if="isOpen" class="modal-overlay" @click="close">
    <div class="modal-content" @click.stop>
      <button class="modal-close" @click="close">×</button>
      <slot></slot>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, watch, defineProps, defineEmits } from 'vue'

// Define the props interface for type safety
interface ModalProps {
  modelValue: boolean
}

// Define props with types
const props = defineProps<ModalProps>()

// Emit an event to update the parent component
const emit = defineEmits<{
  (e: 'update:modelValue', value: boolean): void
}>()

// Reactive state to control the modal visibility
const isOpen = ref<boolean>(props.modelValue)

// Watch for changes in modelValue prop to sync the state
watch(
  () => props.modelValue,
  (newVal) => {
    isOpen.value = newVal
  }
)

// Method to close the modal
const close = () => {
  isOpen.value = false
  emit('update:modelValue', false)
}
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal-content {
  background: white;
  padding: 20px;
  border-radius: 8px;
  max-width: 500px;
  width: 100%;
  position: relative;
}

.modal-close {
  position: absolute;
  top: 10px;
  right: 10px;
  background: none;
  border: none;
  font-size: 18px;
  cursor: pointer;
}
</style>
