<script setup>
import Productlist from '@/components/Productlist.vue'
import { ref } from 'vue'

let productText = ref('')
let productPrice = ref('')
const productList = ref([])

const handleSubmit = () => {
  if (productText.value.trim() !== '') {
    const newObj = { name: productText.value, price: productPrice.value }
    productList.value.push(newObj)
    productText.value = ''
    productPrice.value = ''
  }
}

const handleDelete = data => {
  console.log('received')
  productList.value.splice(data, 1)
}

const handleEdit = ({ index, newProduct }) => {
  productList.value[index].name = newProduct.name
  productList.value[index].price = newProduct.price
}
</script>

<template>
  <div class="container text-center pt-5 poppins-regular">
    <div class="row">
      <div class="col-6 px-5">
        <h1>Add Product</h1>
        <form @submit.prevent="handleSubmit">
          <input
            class="form-control my-5 p-3"
            type="text"
            v-model="productText"
            placeholder="Enter Product name"
            @keydown.enter="handleSubmit"
          />
          <input
            class="form-control mb-5 p-3"
            type="number"
            v-model="productPrice"
            placeholder="Enter Product price"
            @keydown.enter="handleSubmit"
          />
          <button class="btn btn-dark px-5 py-3 text-end" type="submit">
            Add <i class="bi bi-cart-plus"></i>
          </button>
        </form>
      </div>
      <div class="col-6 px-5">
        <h1 class="mb-5">Your Products</h1>
        <Productlist
          :productList="productList"
          @edit-data="handleEdit"
          @delete-data="handleDelete"
        />
      </div>
    </div>

    <div></div>
  </div>
</template>

<style scoped>
h1 {
  margin: 0;
}
</style>
