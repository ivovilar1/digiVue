<template>
  <div id="app">
    <NavBar/>
    <digimon />
    <Footer/>
  </div>
</template>

<script>
import Digimon from './components/Digimon.vue'
import NavBar from './components/NavBar.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Digimon,
    NavBar,
    Footer,
  }
}
</script>

<style>
  * {
    font-family: Helvetica;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }
</style>
