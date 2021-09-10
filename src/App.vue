<template>
  <div id="app">
    <ArcMap/>
  </div>
</template>

<script>
import ArcMap from './components/ArcMap.vue'

export default {
  name: 'App',
  components: {
    ArcMap
  }
}
</script>

<style>
html, body, #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  height: 100%;
  width: 100%;
  margin: 0
}
</style>
