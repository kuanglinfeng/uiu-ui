<template>
  <router-view />
</template>

<script>
import { ref, provide } from 'vue'

export default {
  name: 'App',
  setup() {
    const width = document.documentElement.clientWidth
    const menuVisible = ref(width > 500)
    provide('menuVisible', menuVisible)
  }
}
</script>
