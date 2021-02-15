<template>
  <div id="app">
    <header class="container">
        <div class="row">
            <a href="#">
                <h1>Weather<p>VueApp</p></h1>
            </a>
            <a href=""
               class="btnSearch"
               v-on:click.prevent="handleIsDisabled">
               <span 
                  class="material-icons">
                  {{ isDisabled ?  "close" : "search" }}
               </span>
            </a>
        </div>
    </header>
    <Info/>
    <Search :toggle="isDisabled"/>
    <WeekWeather/>
  </div>
</template>

<script>
  import './assets/styles/default.css';

  import Info from './components/Info.vue';
  import Search from './components/Search.vue';
  import WeekWeather from './components/WeekWeather.vue';

  export default {
    name: 'App',
    data() {
       return {
          isDisabled: false
       }
    },
    components: {
      Info,
      Search,
      WeekWeather
    },
    methods: {
       handleIsDisabled(){ this.isDisabled = !this.isDisabled }
    }
  }
</script>

<style scoped>

/* Header menu on top */
header{
    background-color: #4A4A4A;
    padding: 10px 0px;
}

header a{
    text-decoration: none;
    color: #FFFFFF;
    display: inline-block;
}

header a:hover{
    color: #c4c4c4;
}

header a h1{
    font-size: 18px;
    font-weight: 600;
}

header a h1 p{
    display: inline-block;
    font-weight: 300;
    color: #EC6E4C;
}

header .row{
    display: flex;
    justify-content: space-between;
}

.btnSearch{
   display: flex;
   justify-content: center;
   font-weight: 500;
}

</style>
