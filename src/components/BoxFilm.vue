<template>

    <div class="container">



        <ul>

            <li v-if="info.poster_path == null ">

                poster: <img src="@/assets/img/images.png" alt="">

            </li>

             <li v-else>

                poster: <img :src="'https://image.tmdb.org/t/p/w154' + info.poster_path" :alt="info.original_language">
                
            </li>

            <li>Titolo: {{info.title == null ? info.name : info.title}}</li>
            <li>Titolo originale: {{info.original_title == null ? info.original_name : info.original_title}} </li>
            
            <li v-if="listFlags.includes(info.original_language)">
                
               Lingua:  <img class="flag" :src="require(`@/assets/img/${info.original_language}.png`)" alt="info.original_language">
            
            </li>

            <li v-else>
                
                Lingua: {{info.original_language}} 
                
            </li>

            <li><star-rating :rating="info.vote_average" :star-size="20"  :read-only="true" :increment="0.01" /> {{info.vote_average}}</li>

        </ul>

    </div>

</template>


<script>

    import StarRating from 'vue-star-rating';

    export default {

        name: 'BoxFilm',

        components: {

            StarRating

        },

        props: ['info'],

        data() {

            return {

                listFlags: ['en', 'ja']

            }

        },

        methods: {

            // functionInt(vote) {


            // }

            
            

        }
        
    }

</script>


<style scoped lang="scss">
    
    .container {
        ul {
            li {
                .flag {
                    width: 15px;
                }
            }
        }
    }

</style>