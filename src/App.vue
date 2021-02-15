<template>
  <div id="app">
    <Header/>
    <Info/>
    <Search/>
    <WeekWeather/>
  </div>
</template>

<script>
  import './assets/styles/default.css';

  import Header from './components/Header.vue';
  import Info from './components/Info.vue';
  import Search from './components/Search.vue';
  import WeekWeather from './components/WeekWeather.vue';

  export default {
    name: 'App',
    components: {
      Header,
      Info,
      Search,
      WeekWeather
    }
  }
</script>

<style>
</style>
