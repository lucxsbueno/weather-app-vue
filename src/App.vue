<template>
  <div id="app">
    <Header/>
    <Info/>
  </div>
</template>

<script>
  import './assets/styles/default.css';

  import Header from './components/Header.vue';
  import Info from './components/Info.vue';

  export default {
    name: 'App',
    components: {
      Header,
      Info
    }
  }
</script>

<style>
</style>
