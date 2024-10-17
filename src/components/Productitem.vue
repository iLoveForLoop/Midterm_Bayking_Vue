<script setup>
import { ref } from 'vue'

const props = defineProps({
  product: {},
  index: {},
})

const emit = defineEmits(['delete-data', 'toggle-update'])

const { index } = props

const handleDelete = () => {
  emit('delete-data', index)
}

const handleEditToggle = () => {
  emit('toggle-update', { isEdit: true, index: index })
}
</script>

<template>
  <div
    class="d-flex mt-2 justify-content-between align-items-center bg-body-secondary p-3 rounded"
  >
    <p class="m-0">Name: {{ product.name }}</p>
    <p class="m-0">Price: {{ product.price }}</p>

    <div class="d-flex gap-3">
      <button class="btn btn-dark" @click="handleEditToggle">Edit</button>

      <button class="btn btn-dark" @click="handleDelete">Delete</button>
    </div>
  </div>
</template>

<style scoped>
</style>
