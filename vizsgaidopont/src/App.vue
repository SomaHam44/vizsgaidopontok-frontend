<template>
<div class="container-fluid">
  <h1 class="text-center">Vizsgaidőpontok</h1>
<nav class="navbar">
  <div class="navbar-nav">
  <a href="#tablazat">Táblázat</a>
  <a href="#form">Form</a>
  </div>
</nav>

<VizsgaIdopont/>
<VizsgaIdopontForm/>
</div>
</template>

<script>
import VizsgaIdopont from './components/VizsgaIdopont.vue'
import VizsgaIdopontForm from './components/VizsgaIdopontForm.vue'
export default {
  name: 'App',
  components: {
    VizsgaIdopontForm, VizsgaIdopont
  }
}
</script>

<style>

</style>
