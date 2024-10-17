<script setup>
import { useRouter } from 'vue-router'

const router = useRouter()
</script>

<template>
  <nav
    class="navbar text-dark m-auto d-flex justify-content-between px-5 py-4"
    style="width: 100%"
  >
    <div>
      <router-link class="navbar-brand fs-2 protest co" to="/"
        >MidtermVue</router-link
      >
    </div>

    <div
      class="d-flex justify-content-between align-items-center gap-5 poppins-regular"
    >
      <router-link class="navbar-brand p-0 m-0" to="/productform"
        >Product <i class="bi bi-cart3"></i
      ></router-link>
      <router-link class="navbar-brand p-0 m-0" to="/about">About</router-link>
    </div>
  </nav>
</template>

<style lang="scss"  scoped>
$main-c: rgb(22, 21, 23);

.co {
  color: $main-c;
}
</style>
