
<template>

    <div class="container">

        <header>

            <h2>BoolFlixx</h2>

            <Search @search="searchFilm"/>

        </header>
        
        <h2>FILMS</h2>

        <ul v-for="lista in filterFilm" :key="lista.id">

            <li>Titolo: {{lista.title}}</li>
            <li>Titolo Originale: {{lista.original_title}}</li>
            <li>Lingua: <img :src="'@/assets/img/' + lista.original_language + '.png'" alt=""></li>
            <li>Voto: {{lista.vote_average}}</li>

        </ul>

        <h2>SERIE</h2>

        <ul v-for="lista in filterSerie" :key="lista.id">

            <li>Titolo: {{lista.name}}</li>
            <li>Titolo Originale: {{lista.original_name}}</li>
            <li>Lingua:<img src="@/assets/img/en.png" :alt="lista.original_language">{{lista.original_language}}</li>
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

                apiFilmURL: 'https://api.themoviedb.org/3/search/movie?query=matrix&api_key=a90928149c825de62be6ceef5ce2f3af&language=it-IT',

                apiSerieURL: 'https://api.themoviedb.org/3/search/tv?api_key=a90928149c825de62be6ceef5ce2f3af&language=it_IT&query=a',

                listFilm: [],

                listSerie: [],
                
                searchText: ''

            }

        },

        created() {

            this.getListFilm();

            this.getListSerie();
            
        },

        computed: {

            filterFilm() {

                return this.listFilm.filter(element => {

                    return element.title.toLowerCase().includes(this.searchText.toLowerCase())
                    
                });
                
            },

            filterSerie() {

                return this.listSerie.filter(element => {

                    return element.name.toLowerCase().includes(this.searchText.toLowerCase())
                    
                });

            },

        },

        methods: {

            getListFilm() {

                axios.get(this.apiFilmURL).then(risposta => {

                    this.listFilm = risposta.data.results;
                    
                });
                
            },

            getListSerie() {

                axios.get(this.apiSerieURL).then(risposta => {

                    this.listSerie = risposta.data.results;
                    
                });
                
            },

            searchFilm(searchInput) {
                
                this.searchText = searchInput;

            },
            
        }

    }

</script>


<style scoped lang="scss">

    

</style>