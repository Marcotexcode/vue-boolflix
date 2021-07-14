<template>

    <div class="container">

        <ul>
            
            <li>Titolo: {{info.title == null ? info.name : info.title}}</li>
            <li>Titolo originale: {{info.original_title == null ? info.original_name : info.original_title}} </li>
            
            <li v-if="listFlags.includes(info.original_language)">
                
               Lingua:  <img :src="require(`@/assets/img/${info.original_language}.png`)" alt="info.original_language">
            
            </li>

            <li v-else>
                
                Lingua: {{info.original_language}} 
                
            </li>

            <li>Voto: {{info.vote_average}}</li>

        </ul>

    </div>

</template>


<script>

    export default {

        name: 'BoxFilm',

        props: ['info'],

        data() {

            return {

                listFlags: ['en', 'ja']

            }

        }
        
    }

</script>


<style scoped lang="scss">
    
    .container {
        ul {
            li {
                img {
                    width: 15px;
                }
            }
        }
    }

</style>