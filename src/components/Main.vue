<template>

    <div class="container-fluid">

        <h2>FILM</h2>

        <div class="row justify-content-between p-5">
           
            <BoxFilm v-for="film in films" :key="film.id" :info="film"/>          

        </div>
        
        <h2>SERIE</h2>
        
        <div class="row justify-content-between p-5">
            
            <BoxFilm v-for="serie in series" :key="serie.id" :info="serie"/>
            
        </div>

    </div>

</template>


<script>

    import BoxFilm from '@/components/BoxFilm.vue';

    export default {

        name: 'Main',

        components: {

            BoxFilm,           

        },

        props: {

            films: Array,
            series: Array

        },

    }


</script>


<style scoped lang="scss">

    @import '../style/mixins.scss';

    .container-fluid{
        padding-top: 100px;
        background-color: rgb(37, 37, 37);

        h2 {
            color: white;
        }
    }

</style>