
<template>

    <div>

        <h2>main</h2>

        <ul v-for="lista in listFilm" :key="lista.id">

            <li>{{lista.title}}</li>
            <li>{{lista.original_title}}</li>
            <li>{{lista.original_language}}</li>
            <li>{{lista.vote_average}}</li>

        </ul>

    </div>

</template>


<script>

    import axios from 'axios';

    export default {

        name: 'main',

        data() {

            return {

                apiURL: 'https://api.themoviedb.org/3/search/movie?query=matrix&api_key=a90928149c825de62be6ceef5ce2f3af&language=it-IT',

                listFilm: []

            }

        },

        created() {

            this.getListFilm();

        },

        methods: {

            getListFilm() {

                axios.get(this.apiURL).then(risposta =>{

                    this.listFilm = risposta.data.results;

                    console.log(this.listFilm);
                
                });

            }

        }

    }

</script>


<style scoped lang="scss">

</style>