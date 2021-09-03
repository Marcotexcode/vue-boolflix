<template>

  <div id="app">

    <Header @search="ricercaFilm"/>

    <Main :films="listFilm" :series="listSerie"/>

  </div>

</template>

<script>

  import axios from 'axios';
  import Header from '@/components/Header.vue';
  import Main from '@/components/Main.vue';


  export default {
    name: 'App',

    components: {

      Header,
      Main
    
    },

    data() {

      return {

        apiFilmURL: 'https://api.themoviedb.org/3/search/movie?api_key=a90928149c825de62be6ceef5ce2f3af&language=it-IT',
        apiSerieURL: 'https://api.themoviedb.org/3/search/tv?api_key=a90928149c825de62be6ceef5ce2f3af&language=it-IT',

        apiFilmBase:'https://api.themoviedb.org/3/movie/now_playing?api_key=a90928149c825de62be6ceef5ce2f3af&language=en-US&page=1',
        apiSerieBase:'https://api.themoviedb.org/3/tv/airing_today?api_key=a90928149c825de62be6ceef5ce2f3af&language=en-US&page=1',

        listFilm: [],
        listSerie: []

      }

    },

    created() {

            this.getListFilms();
            this.getListSerie();



        },

    methods: {

      ricercaFilm(text) {

        const request = {
            
          params: {

            query: text

          }
            
        };

        axios.all([

          axios.get(this.apiFilmURL, request),
          axios.get(this.apiSerieURL, request),

        ]).then(axios.spread( (responseMovie, responseSerie) => {

          this.listFilm = responseMovie.data.results;
          this.listSerie = responseSerie.data.results;

        }));

      },

      getListFilms() {

       axios.get(this.apiFilmBase).then(response => {

          this.listFilm = response.data.results;


        })

      },

      getListSerie() {

       axios.get(this.apiSerieBase).then(response => {

          this.listSerie = response.data.results;


        })
        
      }

    }

  }

</script>


<style lang="scss">

  @import '../src/style/commons.scss';

</style>
