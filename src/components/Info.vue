<template>
    <section class="container info-area">
        <article class="row">
            <h2 class="city-weather">Florianópolis, <span>24ºC.</span></h2>
            <p class="date">Segunda-feira, 22 de fevereiro de 2021.</p>
            <p class="desc">parcialmente nublado</p>
            <img src="../assets/02d@2x.svg" alt="">
        </article>
    </section>
</template>

<script>
export default {
    name: 'Info'
}
</script>

<style scoped>
/* Info area top */

.info-area{
    background-color: #4A4A4A;
    color: #FFFFFF;
}

.info-area .city-weather{
    font-size: 30px;
}

.info-area .city-weather span{
    font-weight: 300;
}

/* .info-area .date{ }

.info-area .desc{ } */

.info-area img{
    margin-bottom: 10px;
}
</style>