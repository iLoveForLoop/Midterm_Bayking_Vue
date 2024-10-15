<script setup>
import { useRouter } from 'vue-router'

const router = useRouter()
</script>

<template>
  <nav
    class="navbar bg-body-secondary text-dark m-auto d-flex justify-content-between px-5 py-4"
    style="width: 100%"
  >
    <div>
      <router-link
        class="navbar-brand fs-1 shadows-into-light-regular fw-bold"
        to="/"
        >VueMidterm</router-link
      >
    </div>

    <div
      class="d-flex justify-content-between align-items-center gap-5 poppins-regular"
    >
      <div>
        <router-link class="navbar-brand p-0 m-0" to="/about"
          >About</router-link
        >
      </div>
      <div>
        <router-link class="navbar-brand p-0 m-0" to="/productform"
          >Product<i class="bi bi-cart3 fs-3"></i
        ></router-link>
      </div>
    </div>
  </nav>
</template>

<style scoped>
</style>
