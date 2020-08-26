<template>
  <div>
    <Switch :value="bool" @input="bool = $event" />
  </div>
</template>

<script lang="ts">
import { ref } from 'vue'
import Switch from '../lib/Switch.vue'

export default {
  components: { Switch },
  setup() {
    const bool = ref(true)
    return { bool }
  }
}
</script>