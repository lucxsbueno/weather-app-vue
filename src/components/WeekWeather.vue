<template>
    <section class="container weather-days">
        <div class="row">
            <h3>Previsão para os próximos três dias</h3>
            <div class="grid">
                <article class="box">
                    <span class="day-of-week">Segunda-feira</span>
                    <span class="description">chuva passageira</span>
                    <span class="weather">22ºC</span>
                    <img src="../assets/02d@2x.svg" alt="">
                </article>
                <article class="box">
                    <span class="day-of-week">Terça-feira</span>
                    <span class="description">chuva passageira</span>
                    <span class="weather">20ºC</span>
                    <img src="../assets/02d@2x.svg" alt="">
                </article>
                <article class="box">
                    <span class="day-of-week">Quarta-feira</span>
                    <span class="description">chuva passageira</span>
                    <span class="weather">18ºC</span>
                    <img src="../assets/02d@2x.svg" alt="">
                </article>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    name: 'WeekWeather'
}
</script>

<style scoped>
/* Weather info */

/* .weather-days { } */

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
    border-right: 1px solid #E9E9E9;
}

.weather-days .grid > .box:nth-last-child(1){
    border-right: none;
}

.weather-days .grid .box .day-of-week{
    font-weight: 500;
    font-size: 18px;
}
</style>