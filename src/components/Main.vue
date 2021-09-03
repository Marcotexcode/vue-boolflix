<template>

    <div class="container-fluid">

        <h2>Film</h2>

        <div class="row justify-content-between p-5">
           
            <BoxFilm v-for="film in films" :key="film.id" :info="film"/>          

        </div>
        
        <h2>Serie</h2>
        
        <div class="row justify-content-between p-5">
            
            <BoxSerie v-for="serie in series" :key="serie.id" :info="serie"/>
            
        </div>

    </div>

</template>


<script>

    import BoxFilm from '@/components/BoxFilm.vue';
    import BoxSerie from '@/components/BoxSerie.vue';


    export default {

        name: 'Main',

        components: {

            BoxFilm,
            BoxSerie           

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