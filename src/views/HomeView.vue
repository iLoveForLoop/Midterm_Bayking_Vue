<script setup>
import { ref } from 'vue'

const current = ref(new URL('@/assets/toji.gif', import.meta.url).href)
const hover = ref(new URL('@/assets/toji-hover.gif', import.meta.url).href)
const rest = ref(new URL('@/assets/toji.gif', import.meta.url).href)

const onHover = () => {
  current.value = hover.value
}

const onRest = () => {
  current.value = rest.value
}
</script>

<template>
  <div class="container">
    <div class="row">
      <div
        class="col-6 p-5 d-flex flex-column justify-content-center"
        style="height: 80vh"
      >
        <div>
          <h1 class="protest l-size">Hi I'm Jeferson Bayking</h1>
          <p class="poppins-regular p-size">
            Taking Bachelor of Science in Information Technology, 3rd Year.
          </p>
        </div>
      </div>
      <div
        class="col-6 p-5 d-flex justify-content-center align-items-center"
        style="height: 80vh"
      >
        <div
          class="d-flex flex-columns justify-content-center pb-5"
          @mouseover="onHover"
          @mouseleave="onRest"
        >
          <img class="rounded" :src="current" alt="Logo" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.l-size {
  font-size: 4em;
}

.p-size {
  font-size: 1.5em;
}

.img-size {
  height: 60%;
}
</style>
