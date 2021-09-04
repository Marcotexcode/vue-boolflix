<template>

    <div class="container">

        <h2 class="title-film">Film</h2>

        <hr class="separation">

        <div class="container-films">
           
            <BoxFilm v-for="film in films" :key="film.id" :info="film"/>          

        </div>
        
        <h2 class="title-serie">Serie</h2>

        <hr class="separation">
        
        <div class="container-serie">
            
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
    @import '../style/variabili.scss';

    .container{
        padding-top: 100px;
        background-color: $mainColor;
        text-align: center;

        .title-film, .title-serie {
            margin: 20px 0px;
            font-size: 30px;
            text-transform: uppercase;
            color: $white;
        }

        .separation {
            width: 90%;
            margin: 30px auto 40px;
            height: 5px;
            border-radius: 50px;
            background-color: $white;

        }

        .container-films, .container-serie {
            width: 90%;
            margin: 0 auto;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
        }
        
    }

</style>