<template>
  <div id="app">
    <Ex01Page></Ex01Page>
    <Ex02Page></Ex02Page>
    <Ex03Page></Ex03Page>
  </div>
</template>

<script>
import Ex01Page from './components/ex01/Ex01Page.vue'
import Ex02Page from './components/ex02/Ex02Page.vue'
import Ex03Page from './components/ex03/Ex03Page.vue'

export default {
  name: 'app',
  components: {
    Ex01Page,
    Ex02Page,
    Ex03Page
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
