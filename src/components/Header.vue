
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

                <div @click="isActive = !isActive" :class="(isActive === true) ? 'active' : 'not-active'" class="btn2">

                    <i class="search-btn fas fa-times"></i>

                </div>

                <input v-on:keyup="$emit('search', inputText)" class="" :class="(isActive === false) ? 'active-text' : 'search-text'" type="text" placeholder="Scegli il film" v-model.trim="inputText">

                <div @click="isActive = !isActive" :class="(isActive === true) ? 'not-active' : 'active'" class="btn">

                    <i class="search-btn fas fa-search"></i>

                </div>
                
            </form>

        </div>        
        
    </div>

</template>


<script>
    
    export default {

        name: 'Header',

        data() {

            
            return {
                isActive: true,
                inputText: '',
                

            }

        },

        methods: {
            


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
        
        background-color: rgb(20, 20, 20);;
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

            .btn{
                margin: 0px 20px;
                color: white;
                position: absolute;
                right: 0;
                z-index: 10;
                font-size: 20px;
                cursor: pointer;
            }

            .btn2{
                cursor: pointer;
                margin: 0px 10px;
                color: white;
                left: 0;
                z-index: 10;
                font-size: 20px;
            }

        }

        form {
            position: relative;
            display: flex;
            align-items: center;

            button {
                @include button (black);
            }

            .search-text {
                display: block;
                @include input (black);
                padding: 10px;
                border-radius: 20px;
                transition: all 0.5s;
                background-color: rgba(0, 0, 0, 0.753);
                color: white;
                outline: none;
            }

            .active-text {
                padding: 0;
                width: 0;
                opacity: 0;
                transition: all 0.5s;
            }

            .not-active {
                display: none;
            }

            input:focus {
                border: none;   
            }
            
        }

    }

</style>