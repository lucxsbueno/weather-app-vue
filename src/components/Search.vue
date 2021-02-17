<template>
    <section class="container search" v-bind:class="[toggle ? active : disabled]">
        <div class="row">
            <form action="" method="POST">
                <label for="search"></label>
                <input
                    type="text"
                    name="search"
                    id="inputSearch"
                    placeholder="Pesquise o clima de outra cidade."
                    autocomplete="off"
                    v-model="search"
                    >
                <input type="submit" value="PESQUISAR" v-on:click.prevent="handleSearch">
                <!--<button class="material-icons" v-on:click.prevent="handleToggle(toggle)">close</button>-->
            </form>
        </div>
    </section>
</template>

<script>
export default {
    name: 'Search',
    data(){
        return{
            search: '',
            active: 'active',
            disabled: 'disabled'
        }
    },
    methods: {
        handleSearch: function(){
            this.$emit("searchApi", {
                args: this.search
            });
        },
        handleToggle: function(){
            return this.toggle = !this.toggle 
        }
    },
    props: {
        toggle: Boolean
    }
}
</script>

<style scoped>
.active{
    display: flex;
}

.disabled{
    display: none;
}

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
    background-color: rgb(205, 205, 205, 16%);
    border: 3px solid rgb(205, 205, 205, 1%);
    font-size: 16px;
    padding: 8px 10px;
    color: #FFFFFF;
    margin-right: 15px;
    width: 100%;
    transition: 0.3s all;
}

.search form input[type=text]:focus{
    border: 3px solid #B0B0B0;
    transition: 0.3s all;
}

.search form input[type=text]::placeholder{
    color: #DEDEDE;
}

.search form input[type=submit]{
    background-color: #EC6E4C;
    border: 3px solid #EC6E4C;
    border-radius: 4px;
    /* margin-right: 15px; */
    font-size: 16px;
    color: #FFFFFF;
    padding: 8px 15px;
    font-weight: 500;
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