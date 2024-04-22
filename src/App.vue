<template>
  <RegistrationForm />
  <SidebarMenu />
</template>

<script>
import SidebarMenu from './components/SidebarMenu.vue'
import RegistrationForm from './components/RegistrationForm.vue'

export default {
  name: 'App',
  components: {
    SidebarMenu,
    RegistrationForm
  }
}
</script>

<style>
#app {
  font-family: "Noto Sans JP",Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
