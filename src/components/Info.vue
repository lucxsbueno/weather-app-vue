<template>
    <section class="container info-area">
        <article class="row">
            <h2 class="city-weather">{{ name }}, <span>{{ temp | toInt}}ºC.</span></h2>
            <p class="date">{{ timestamp | convert }}</p>
            <p class="desc">{{ description }}</p>
            <img :src="`http://openweathermap.org/img/wn/${icon}@2x.png`" alt="">
        </article>
    </section>
</template>

<script>
export default {
    name: 'Info',
    props: {
        name: String,
        temp: Number,
        timestamp: Number,
        description: String,
        icon: String
    },
    filters: {
        convert: function(value){
            var d = new Date(value * 1000);
            var options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
            var now = d.toLocaleDateString('pt-BR', options);
            var nowToUppercase = now[0].toUpperCase() + now.substring(1) + ".";
            return nowToUppercase;
        },
        toInt: function(value){
            return parseInt(value);
        }
    }
}
</script>

<style scoped>
/* Info area top */

.info-area{
    background-color: #4A4A4A;
    color: #FFFFFF;
}

.info-area img{
    width: 50px
}

.info-area .city-weather{
    font-size: 30px;
}

.info-area .city-weather span{
    font-weight: 300;
}

/* .info-area .date{ }

.info-area .desc{ } */
</style>