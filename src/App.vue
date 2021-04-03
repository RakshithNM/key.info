<template>
  <KeyCode title="key.info" />
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import KeyCode from './components/KeyCode.vue'

export default defineComponent({
  name: 'App',
  components: {
    KeyCode 
  }
})
</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #011627;
  color: #8cc5ff;
  height: 100vh;
  overflow: hidden;
}
</style>
