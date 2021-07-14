<template>

    <div class="container">

        
        <h2>FILM</h2>

        <div class="container-box">

            <BoxFilm v-for="film in films" :key="film.id" :info="film"/>
            
        </div>

        <h2>SERIE</h2>
        
        <div class="container-box">
            
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

        }

    }

</script>


<style>

</style>