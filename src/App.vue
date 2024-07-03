<template>
  <MaquetaInterfaz />
</template>

<script>
import MaquetaInterfaz from './components/MaquetaInterfaz.vue'

export default {
  name: 'App',
  components: {
    MaquetaInterfaz
  }
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  background-color: black;
}

main{
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
