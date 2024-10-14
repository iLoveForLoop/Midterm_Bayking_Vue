<script setup>
import { ref } from 'vue'
import Productitem from './Productitem.vue'
import Editpage from './Editpage.vue'

const emit = defineEmits(['delete-data', 'edit-data'])
const props = defineProps({
  productList: {},
})

const { productList } = props

let currentIndex = ref(0)
let isShow = ref(false)

const handleEdit = newProduct => {
  console.log(newProduct)
  console.log(currentIndex)
  if (newProduct.trim() !== '') {
    console.log('tried to edit')
    emit('edit-data', { index: currentIndex.value, newProduct: newProduct })
    isShow.value = false
    console.log('i reached the buttom')
  }
}

const handleToggle = ({ isEdit, index }) => {
  isShow.value = isEdit
  currentIndex.value = index
}

const handleDelete = data => {
  emit('delete-data', data)
}
</script>

<template>
  <Editpage @toggle-edit="handleToggle" @edit-data="handleEdit" v-if="isShow" />

  <Productitem
    v-for="(task, index) in productList"
    :key="index"
    :task="task"
    :index="index"
    @delete-data="handleDelete"
    @toggle-update="handleToggle"
  />
</template>

<style scoped></style>
