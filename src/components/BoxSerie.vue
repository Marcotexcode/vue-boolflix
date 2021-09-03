<template>

    <div class="container-box">
     
        <ul class="p-3">
           
            <div class="box-foto" v-if="info.poster_path == null ">

                <img class="nofound" src="@/assets/img/images.png" alt="">

            </div>
                
            <div class="box-foto" v-else>

                <img :src="'https://image.tmdb.org/t/p/w154' + info.poster_path" :alt="info.original_language">

            </div>
            
            <div class="list-info">

            <li> <strong>Titolo: </strong> {{info.title == null ? info.name : info.title}}</li>
            <li> <strong>Titolo originale:</strong> {{info.original_title == null ? info.original_name : info.original_title}} </li>
            
            <li v-if="listFlags.includes(info.original_language)">
                
              <strong>Lingua: </strong> <img class="flag" :src="require(`@/assets/img/${info.original_language}.png`)" alt="info.original_language">
            
            </li>

            <li v-else>
                
                Lingua: {{info.original_language}} 
                
            </li>

            <li><star-rating :rating="info.vote_average" :star-size="20"  :read-only="true" :increment="0.01" /></li>
            
            </div>
        
        </ul>

    </div>

</template>


<script>

    import StarRating from 'vue-star-rating';

    export default {

        name: 'BoxSerie',

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

    .container-box:hover .list-info {
                
        display: block;

    }

    .container-box {
        width: 250px;
        height: 339px;
        margin-bottom: 20px;
        
        .box-foto {

            width: 100%;
                height: 100%;
                
            img {
                width: 100%;
                height: 100%;
                
            }

        }

        ul {            
            width: 100%;   
            height: 100%;         
            background-color: rgb(73, 73, 73);
            color: white;
            position: relative;

            .list-info{
                display: none;
                position: absolute;
                top: 0;
                left: 0;
                background-color: rgba(0, 0, 0, 0.651);
                width: 100%;
                height: 100%;
                padding: 10px;
            
                li {
                    list-style: none;
                    margin: 10px 0px;

                    .nofound {
                        width: 100%;
                        height: 100%;
                    }
                    
                    .flag {
                        width: 15px;
                    }

                }

            }

        }

    }

</style>