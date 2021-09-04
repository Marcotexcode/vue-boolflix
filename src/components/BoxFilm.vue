<template>

    <div class="container-box">
     
        <ul class="">
           
            <div class="box-foto" v-if="info.poster_path == null ">

                <img class="nofound" src="@/assets/img/images.png" alt="">

            </div>
                
            <div class="box-foto" v-else>

                <img :src="'https://image.tmdb.org/t/p/w154' + info.poster_path" :alt="info.original_language">

            </div>
            
            <div class="list-info">

                <li><strong>Titolo </strong></li>
                <li>{{info.title == null ? info.name : info.title}}</li>

                <li><strong>Titolo originale</strong></li>
                <li>{{info.original_title == null ? info.original_name : info.original_title}}</li>
                
                <li v-if="listFlags.includes(info.original_language)"><strong>Lingua </strong></li>
                <li v-else><strong>Lingua: </strong> {{info.original_language}}</li>
                <li><img class="flag" :src="require(`@/assets/img/${info.original_language}.png`)" alt="info.original_language"></li>

                <li><star-rating :rating="info.vote_average" :star-size="20"  :read-only="true" :increment="0.01" /></li>
            
            </div>
        
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
        
    }

</script>


<style scoped lang="scss">

    @import '@/style/mixins.scss';

    @include box();

</style>