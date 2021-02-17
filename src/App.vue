<template>
  <div id="app" v-cloak>

    <div v-if="errorStr" class="page" v-cloak>
      <div>
        <h2 class="title">Oops...</h2>
        <p class="msg">
          Você precisa ativar o serviço de localização
          para prosseguir!
        </p>
        <img src="./assets/imgs/not-found.svg" alt="">
      </div>
    </div>
    
    <div v-if="gettingLocation" class="page" v-cloak>
      <div>
        <h2 class="title">Obtendo sua localização...</h2>
        <p class="msg">
          Fique tranquilo, nós só precisamos dela para informar a
          você o clima da sua cidade!
        </p>
        <img src="./assets/imgs/location.svg" alt="">
      </div>
    </div>

    <header class="container" v-if="location">
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

    <Info
      v-if="location"
      :name="this.data.city.name"
      :timestamp="this.data.list[0].dt"
      :description="this.data.list[0].weather[0].description"
      :temp="this.data.list[0].main.temp"
      :icon="this.data.list[0].weather[0].icon"/>

    <Search :toggle="isDisabled" @searchApi="handleSearch($event)"/>

    <WeekWeather :list="this.data.list" :v-if="list"/>
  </div>
</template>

<script>
  import axios from 'axios';

  import './assets/styles/default.css';

  import Info from './components/Info.vue';
  import Search from './components/Search.vue';
  import WeekWeather from './components/WeekWeather.vue';

  export default {
    name: 'App',
    components: {
      Info,
      Search,
      WeekWeather
    },
    data: function() {
        return {
          data: [],
          // input toggle
          isDisabled: false,
          // geolocation
          location: null,
          gettingLocation: false,
          errorStr: null,
          city: null
        }
    },
    created: function() {

      //do we support geolocation
      if(!("geolocation" in navigator)) {
        this.errorStr = 'Geolocation is not available.';
        return;
      }

      this.gettingLocation = true;

      // get position
      navigator.geolocation.getCurrentPosition(pos => {
        this.gettingLocation = false;
        this.location = pos;
       
        axios.get(`https://maps.googleapis.com/maps/api/geocode/json?latlng=${this.location.coords.latitude.toFixed(7)},${this.location.coords.longitude.toFixed(7)}&sensor-false&key=${process.env.GOOGLE_KEY}`)
        .then(res => {
          this.city = res.data.results[0].address_components[4].long_name;
          axios.get(`http://api.openweathermap.org/data/2.5/forecast?q=${this.city}&lang=pt_br&exclude=hourly,minutely&units=metric&appid=${process.env.WEATHER_KEY}`)
            .then(res => {
              this.data = res.data;
              for (let i = 0; i < this.data.list.length; i++) {
                this.data.list.splice(i, 7);
              }
            })
            .catch(error => {
              console.log(error);
            });
        });
      }, err => {
        this.gettingLocation = false;
        this.errorStr = err.message;
      })

    },
    methods: {
      handleIsDisabled: function() { 
        this.isDisabled = !this.isDisabled
      },
      handleSearch($event){
        console.log($event.args);
        axios.get(`http://api.openweathermap.org/data/2.5/forecast?q=${$event.args}&lang=pt_br&exclude=hourly,minutely&units=metric&appid=d12ffd27adaf782a4e2f467414e9eeb1`)
          .then(res => {
            this.data = res.data;
          })
          .catch(error => {
            console.log(error);
          });
      }
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

/* Getting location page */

.page{
  position: absolute;
  width: 100%; 
  bottom: 0;
  top: 0;
  background-color: #4A4A4A;
  display: flex;
  justify-content: center;
  align-items: center;
}

.page div{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.page div img{
  margin-left: -30px;
  margin-top: 20px;
}

.page .title{
  font-size: 22px;
  font-weight: 500;
  margin-bottom: 10px;
  text-align: center;
  color: #F2F2F2;
}

.page .msg{
  font-size: 16px;
  font-weight: 300;
  max-width: 400px;
  text-align: center;
  margin-bottom: 15px;
  line-height: 22px;
  color: #FFFFFF;
}

.page a{
  text-decoration: none;
  color: #FFFFFF;
  margin-top: 20px;
}

.page a:hover{
  text-decoration: underline;
}

</style>
