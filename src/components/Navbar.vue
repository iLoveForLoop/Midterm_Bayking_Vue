<script setup>
import { useRouter } from 'vue-router'

const router = useRouter()
</script>

<template>
  <nav
    class="navbar bg-body-secondary text-dark m-auto d-flex justify-between px-5"
  >
    <div class="d-flex">
      <div>
        <router-link class="navbar-brand" to="/">Home</router-link>
      </div>
      <div>
        <router-link class="navbar-brand" to="/about">About</router-link>
      </div>
      <div>
        <router-link class="navbar-brand" to="/productlist"
          >Product List</router-link
        >
      </div>
    </div>
  </nav>
</template>

<style></style>
