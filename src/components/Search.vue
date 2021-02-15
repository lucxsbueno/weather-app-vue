<template>
    <section class="container search">
        <div class="row">
            <form action="" method="POST">
                <label for="search"></label>
                <input type="text" name="search" id="inputSearch"
                    placeholder="Pesquise o clima de outra cidade.">
                <input type="submit" value="PESQUISAR">
                <button class="material-icons">close</button>
            </form>
        </div>
    </section>
</template>

<script>
export default {
    name: 'Search'
}
</script>

<style scoped>
.search{
    background-color: #4A4A4A;
}

.search .row form{
    display: flex;
    align-items: center;
    padding-bottom: 15px;
}

.search form input[type=text]{
    border-radius: 4px;
    background-color: rgb(170, 170, 170, 64%);
    border: 3px solid #616161;
    font-size: 16px;
    padding: 8px 10px;
    color: #FFFFFF;
    margin-right: 15px;
    width: 100%;
}

.search form input[type=text]::placeholder{
    color: #DEDEDE;
}

.search form input[type=submit]{
    background-color: #EC6E4C;
    border: 3px solid #EC6E4C;
    border-radius: 4px;
    font-size: 16px;
    color: #FFFFFF;
    padding: 8px 15px;
    font-weight: 500;
    margin-right: 15px;
    cursor: pointer;
}

.search form input[type=submit]:hover{
    background-color: #f08162;
    border: 3px solid #f08162;
}

.search form button{
    background-color: transparent;
    border: 3px solid transparent;
    border-radius: 4px;
    font-size: 24px;
    color: #FFFFFF;
    padding: 8px 10px;
    cursor: pointer;
}

.search form button:hover{
    background-color: #616161;
    border: 3px solid #616161;
}
</style>