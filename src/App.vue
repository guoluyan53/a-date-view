<template>
  <div id="app">
    <HelloWorld/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
/* #app{
  color:#4a59ff;
} */
html,body{
  margin: 0;
  padding: 0;
  font-size: calc(100vw / 100);
  background-color: #141516;
  color: white;
  overflow-x: hidden;
}
</style>
