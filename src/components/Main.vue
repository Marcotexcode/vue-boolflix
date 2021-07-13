
<template>

    <div>

        <h2>main</h2>

        <Search @search="searchFilm"/>

        <h2>FILMS</h2>

        <ul v-for="lista in filterFilm" :key="lista.id">

            <li>Titolo: {{lista.title}}</li>
            <li>Titolo Originale: {{lista.original_title}}</li>
            <li>Lingua: <img :src="flag" width='15px'></li>
            <li>Voto: {{lista.vote_average}}</li>

        </ul>

        <h2>SERIE</h2>

        <ul v-for="lista in filterSerie" :key="lista.id">

            <li>Titolo: {{lista.name}}</li>
            <li>Titolo Originale: {{lista.original_name}}</li>
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

                apiFilmURL: 'https://api.themoviedb.org/3/search/movie?query=matrix&api_key=a90928149c825de62be6ceef5ce2f3af&language=it-IT',

                apiSerieURL: 'https://api.themoviedb.org/3/search/tv?api_key=a90928149c825de62be6ceef5ce2f3af&language=it_IT&query=a',

                listFilm: [],

                listSerie: [],

                flag: '',

                listFlags: [ 
                    
                    {
                
                        en:'@/assets/img/en.png'
                        
                    },

                    {
                        
                        ja:'@/assets/img/ja.png'

                    }

                ],
                
                searchText: ''

            }

        },

        created() {

            this.getListFilm();

            console.log('url: ' + this.flag);

            //console.log(this.listFlags);

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

            // filtFlags() {

            //     return this.listFilm.filter(element => {

            //     if(this.element.original_language.includes(this.listFlags)) {

            //         return element.original_language = this.listFlags

            //     }
                
            //     });


            // }

            // filterFlags() {

            //     return this.listFilm.filter(element => {
                
            //     return this.element.original_language.includes(this.listFlags)

            //     })
            // }

        },

        methods: {

            getListFilm() {

                axios.get(this.apiFilmURL).then(risposta => {

                    this.listFilm = risposta.data.results;

                    console.log(this.listFilm);
                    
                });
                
            },

            getListSerie() {

                axios.get(this.apiSerieURL).then(risposta => {

                    this.listSerie = risposta.data.results;

                     console.log(this.listSerie);
                    
                });
                
            },

            searchFilm(searchInput) {
                
                this.searchText = searchInput;

                // console.log(this.searchText);
              
            },


            // PROVA 1

            // search() {

            //     this.listFilm.filter((element) => {
                    
            //         if (this.element.original_language.includes(this.listFlags)) {

            //             element.original_language = 'ciao';

            //         } else {

            //             element.original_language = 'hello';

            //         }

            //     });
           
            // }   
            

            // PROVA 2

            // flag() {

            //     if (this.listFilm.filter.original_language = en ) {

            //         flag = '@/assets/img/en.png'

            //     }

            //     return

            // }

            
        }

    }

</script>


<style scoped lang="scss">

</style>