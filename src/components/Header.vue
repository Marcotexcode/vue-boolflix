
<template>

    <div class="container">
        
        <div class="logo-menu">

            <img class="logo" src="@/assets/img/logo.png" alt="">

            <div class="container-menu">

                <ul class="menu">

                    <li class="menu-list"><a class="menu-link" href="#">Home</a></li>
                    <li class="menu-list"><a class="menu-link" href="#">Serie TV</a></li>
                    <li class="menu-list"><a class="menu-link" href="#">Film</a></li>
                    <li class="menu-list"><a class="menu-link" href="#">Nuovi e popolari</a></li>
                    <li class="menu-list"><a class="menu-link" href="#">La mia lista</a></li>

                </ul>

            </div>

        </div>        

        <div class="container-form">

            <form>

                <input type="text" placeholder="Scegli il film" v-model.trim="inputText">

                <i class="search fas fa-search"></i>


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

    .container {
        display: flex;
        justify-content: space-between;
        align-items: center;
        width: 100%;
        background-color: rgb(58, 50, 50);
        padding: 10px 20px;

        .logo-menu {
            display: flex;
            justify-content: space-around;
            align-items: center;

            .logo {
                width: 85px;
                height: 25px;
                margin-right: 20px;
            }

            .container-menu {

                .menu {
                    display: flex;

                    .menu-list {
                        margin: 20px;
                        list-style: none;

                        .menu-link {
                            text-decoration: none;
                            color: $white;
                        }

                    }
                    
                }

            }

        }

        .container-form {

            .search{
                margin: 0px 20px;
                color: $white;

            }

        }

        form {
            display: flex;
            align-items: center;

            button {
                @include button (black);
            }

            input {
                @include input (black);
                padding: 10px;
            }

            input:focus {
                border: none;   
            }
            
        }

    }

</style>