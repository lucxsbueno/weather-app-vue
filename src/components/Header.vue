<template>
    <header class="container">
        <div class="row">
            <a href="#">
                <h1>Weather<p>VueApp</p></h1>
            </a>
            <a href="#">Pesquisar</a>
        </div>
    </header>    
</template>

<script>
    export default {
        name: 'Header'
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

</style>