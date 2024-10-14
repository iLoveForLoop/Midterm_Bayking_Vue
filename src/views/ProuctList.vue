<script setup>
import Itemlist from '@/components/Itemlist.vue'
import { ref } from 'vue'

let productText = ref('')
let productPrice = ref('')
const productList = ref([{ name: 'water', price: 100 }])

const handleSubmit = () => {
  if (productText.value.trim() !== '') {
    const newObj = { name: productText.value, price: productPrice.value }
    productList.value.push(newObj)
    productText.value = ''
    productPrice.value = ''
  }
}

// const handleSubmit = (data) => {
//   productList.value = data
//   if (productText.value.trim() !== '') {
//     productList.value.push(productText.value)
//     productText.value = ''
//   }
// }

const handleDelete = data => {
  console.log('received')
  productList.value.splice(data, 1)
}

const handleEdit = ({ index, newTask }) => {
  productList.value[index] = newTask
}
</script>

<template>
  <div class="container text-center pt-5">
    <h1>Product List</h1>
    <form @submit.prevent="handleSubmit">
      <input
        type="text"
        v-model="productText"
        placeholder="Enter Product name"
        @keydown.enter="handleSubmit"
      />
      <input
        type="number"
        v-model="productPrice"
        placeholder="Enter Product price"
        @keydown.enter="handleSubmit"
      />
      <button type="submit">Add</button>
    </form>
    <div class="m-auto">
      <Itemlist
        :productList="productList"
        @edit-data="handleEdit"
        @delete-data="handleDelete"
      />
    </div>
  </div>
</template>

<style scoped>
h1 {
  margin: 0;
}

input {
  margin: 10px 10px;
  padding: 10px 15px;
  font-size: 18px;
}

button {
  padding: 5px 20px;
}

form {
  padding: 10px;
}
</style>
