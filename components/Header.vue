<template>
    <header>
        <Loupe v-if="$route.name === 'blog' " @toggle="toggleSearch" />
        <Search @toggle="toggleSearch" :isSearchActive="isSearchActive" />
        <nuxt-link to="/blog"><BackArrow v-if="$route.name === 'post' || $route.name === 'Search' " /></nuxt-link>
        <nuxt-link to="/blog"><BackArrow v-if="this.$route.name === 'post'" /></nuxt-link>

        <div @click="toggleMenu" class="menu" v-bind:class="{active: isMenuActive}"  > 
           <div class="line top"></div> 
           <div class="line center"></div> 
           <div class="line bottom"></div> 
        </div>
    <Nav @viewChange="toggleMenu" :isMenuActive="isMenuActive" />
    </header>

</template>

<script>
export default {

    data: function(){
        return {
            isMenuActive: false,
            isSearchActive: false,

        }
    },

    methods: {
        toggleMenu: function(event){
            this.isMenuActive = !this.isMenuActive;
            this.isSearchActive = false
            console.log(this.$route);
            
        },
        toggleSearch: function(event){
            this.isSearchActive = !this.isSearchActive;
            this.isMenuActive = false;



        }
    }
}
</script>

<style scoped>
 
    
    .menu {
        width: 40px;
        cursor: pointer;
        position: absolute;
        right: 25px;
        top: 20px;
        z-index: 1000;
    }

    .menu.active {
        position: fixed;
    }

    @media(min-width: 600px){
        .menu.active {
            position: absolute;
        }
    }
   

   

    .line {
        height: 5px;
        background: #222;
        margin: 5px 0;
        border-radius: 10px;
        transition: .2s;

    }

    .menu.active .center{
        animation: center .5s ease-in-out;
        transform: translateX(60px);
        opacity: 0;

    
    }

    .menu.active .top{
        animation: top .5s ease-in-out;
        transform: rotate(-45deg) translateY(14px);
  
    }

    .menu.active .bottom{
        animation: bottom .5s ease-in-out;
        transform: rotate(45deg) translateY(-14px);
    }


    

   
</style>