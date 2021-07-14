<template>

    <div class="container-box">

        <ul>

            <li v-if="info.poster_path == null ">

                <img class="nofound" src="@/assets/img/images.png" alt="">

            </li>

             <li v-else>

                <img :src="'https://image.tmdb.org/t/p/w154' + info.poster_path" :alt="info.original_language">
                
            </li>

            <li>Titolo: {{info.title == null ? info.name : info.title}}</li>
            <li>Titolo originale: {{info.original_title == null ? info.original_name : info.original_title}} </li>
            
            <li v-if="listFlags.includes(info.original_language)">
                
               Lingua:  <img class="flag" :src="require(`@/assets/img/${info.original_language}.png`)" alt="info.original_language">
            
            </li>

            <li v-else>
                
                Lingua: {{info.original_language}} 
                
            </li>

            <li><star-rating :rating="info.vote_average" :star-size="20"  :read-only="true" :increment="0.01" /></li>

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

        }
        
    }

</script>


<style scoped lang="scss">
    
    .container-box {
        width: 250px;
        margin-bottom: 20px;
        
        ul {
            display: inline-block;
            padding: 10px;
            text-align: center;
            width: 100%;
            height: 100%;
            background-color: rgb(73, 73, 73);
            color: white;

            li {

                .nofound {

                    width: 154px;

                }
                list-style: none;

                .flag {
                    width: 15px;
                }
            }
        }
    }

</style>