<template>
  
    <div>

        <form>

            <div class="input">

                <input type="text" placeholder="Scegli il film" v-model="inputText">

            </div>

            <div class="button">

                <button type="submit" @click.prevent="$emit('search', inputText)">Invio</button>

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