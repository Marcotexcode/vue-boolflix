
<template>

    <div>

        <h2>main</h2>

        <Search @search="searchFilm"/>

        <ul v-for="lista in filterFilm" :key="lista.id">

            <li>Titolo: {{lista.title}}</li>
            <li>Titolo Originale: {{lista.original_title}}</li>
            <li>Lingua: {{lista.original_language}}</li>
            <li>Voto: {{lista.vote_average}}</li>

        </ul>

    </div>

</template>


<script>

    import Search from '../components/Search.vue';
    import axios from 'axios';

    export default {

        name: 'main',

        components: {

            Search

        },

        data() {

            return {

                apiURL: 'https://api.themoviedb.org/3/search/movie?query=matrix&api_key=a90928149c825de62be6ceef5ce2f3af&language=it-IT',

                listFilm: [],

                searchText: ''

            }

        },

        created() {

            this.getListFilm();
            
        },

        computed: {

            filterFilm() {

                return this.listFilm.filter(element => {

                    return element.title.toLowerCase().includes(this.searchText.toLowerCase())
                    
                });
                
            }

        },

        methods: {

            getListFilm() {

                axios.get(this.apiURL).then(risposta =>{

                    this.listFilm = risposta.data.results;

                  //  console.log(this.listFilm);
                    
                });
                
            },

            searchFilm(searchInput) {
                
                this.searchText = searchInput;
              //  console.log(this.searchText);
              
            },

            

        }

    }

</script>


<style scoped lang="scss">

</style>