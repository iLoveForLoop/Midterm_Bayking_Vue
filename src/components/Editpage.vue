<script setup>
import { ref } from 'vue'

const emit = defineEmits(['edit-data', 'toggle-edit'])

const props = defineProps({
  list: {},
  index: {},
})

let editedName = ref(props.list[props.index].name)
let editedprice = ref(props.list[props.index].price)

const handleSubmit = () => {
  const tmp = { name: editedName.value, price: editedprice.value }
  emit('edit-data', tmp)
  editedName.value = ''
  editedprice.value = ''
}

const toggleEdit = () => {
  emit('toggle-edit', false)
}
</script>

<template>
  <div class="backdrop" @click.self="toggleEdit">
    <div class="edit">
      <form @submit.prevent="handleSubmit">
        <h1>Edit Product</h1>
        <input
          type="text"
          v-model="editedName"
          placeholder="Edit Product"
          @keydown.enter="handleSubmit"
        />
        <input
          type="number"
          v-model="editedprice"
          placeholder="Edit Product"
          @keydown.enter="handleSubmit"
        />
        <button type="submit">Edit</button>
      </form>
    </div>
  </div>
</template>

<style scoped>
.backdrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.5);
  align-content: center;
}

.edit {
  width: 50%;
  height: 50vh;
  background: aliceblue;
  margin: auto;
  text-align: center;
  align-content: center;
}

input {
  padding: 10px 25px;
  font-size: 15px;
}

button {
  padding: 10px 25px;
  margin-left: 20px;
}
</style>
