<template>
    <section class="container weather-days">
        <div class="row">
            <h3>Previsão para os próximos {{ list.length }} dias</h3>
            <div class="grid">
                <article class="box" v-for="(item, index) in list" :key="index">
                    <span class="day-of-week">{{ item.dt | convert() }}</span>
                    <span class="description">{{ item.weather[0].description }}</span>
                    <span class="weather">{{ item.main.temp | toInt() }}</span>
                    <img :src="`http://openweathermap.org/img/wn/${item.weather[0].icon}@2x.png`" alt="">
                </article>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    name: 'WeekWeather',
    props: {
        list: Array
    },
    filters: {
        convert: function(value){
            var d = new Date(value * 1000);
            var options = { weekday: 'long'};
            var now = d.toLocaleDateString('pt-BR', options);
            var nowToUppercase = now[0].toUpperCase() + now.substring(1);
            return nowToUppercase;
        },
        toInt: function(value){
            return parseInt(value)+"ºC";
        }
    }
}
</script>

<style scoped>
/* Weather info */
.weather-days {  }

.weather-days h3{
    padding: 20px 0px;
    display: block;
    font-size: 18px;
    color: #4A4A4A;
    border-bottom: 1px solid #E9E9E9;
    margin-bottom: 20px;
}

.weather-days .grid{
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(186px, auto));

}

.weather-days .grid > .box{
    color: #4A4A4A;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 10px;
}

.weather-days .grid > .box:nth-last-child(1){
    border-right: none;
}

.weather-days .grid .box .day-of-week{
    font-weight: 500;
    font-size: 18px;
}

.box img{
    width: 80px;
}
</style>