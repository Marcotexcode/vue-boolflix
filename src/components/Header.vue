
<template>

    <div class="container-head">
        
        <div class="col12 p-3 d-flex justify-content-between">

            <img src="https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" alt="">

            <form>

                <input type="text" placeholder="Scegli il film" v-model.trim="inputText">

                <button type="submit" @click.prevent="$emit('search', inputText)" @click="reset">Invio</button>

            </form>

        </div>        
        
    </div>

</template>


<script>

    export default {

        name: 'Header',

        data() {

            return {

                inputText: ''

            }

        },

        methods: {
            
            reset() {

                this.inputText = ''
                
            }

        }

    }

</script>


<style scoped lang="scss">


    @import '../style/variabili.scss';
    @import '../style/mixins.scss';

    .container-head{
        
        width: 100%;
        background-color: rgb(58, 50, 50);

        img {
            width: 100px;
        }

        form {
            display: flex;

            

            button {

                @include button (black);

            }

            input {
                @include input (black);
            }

            input:focus {
                border: none;
             
            }
            

        }
    }

</style>