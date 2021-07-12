<template>
  
    <div>

        <form>

            <div class="input">

                <input type="text" placeholder="Scegli il film" v-model.trim="inputText">

            </div>

            <div class="button">

                <button type="submit" @click.prevent="$emit('search', inputText)" @click="reset">Invio</button>

            </div>

        </form>

    </div>

</template>


<script>

    export default {

        name: 'Search',

        data() {

            return {

                inputText:''

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

    form {
        display: flex;

        .input {
            margin: 0px 10px;
        }
    }
    

</style>