<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <SidebarMenu />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import SidebarMenu from './components/SidebarMenu.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    SidebarMenu
  }
}
</script>

<style>
#app {
  font-family: "Noto Sans JP",Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
</style>
