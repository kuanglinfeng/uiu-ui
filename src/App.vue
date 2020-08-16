<template>
  <div>导航栏 | 
    <router-link to='/'>Test</router-link>
    <router-link to='/xxx'>Test2</router-link>
  </div>
  <hr />
  <router-view />
</template>

<script>
import Test from './components/Test.vue'

export default {
  name: 'App'
}
</script>
