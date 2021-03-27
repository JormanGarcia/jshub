<template>
<div class="nav-container" :class="{active: isMenuActive}">

    <nav>
        <div @click="$emit('viewChange')">
            <nuxt-link to="/">Home</nuxt-link>   
        </div>
        <div @click="$emit('viewChange')">
            <nuxt-link to="/Blog">My Blog</nuxt-link>
        </div>
    </nav>

</div>
</template>

<script>
export default {
    props: {
        isMenuActive: Boolean
    }
}
</script>

<style>
    .nav-container {
        width: 100vw;
        height: 100vh;
        visibility: hidden;

        transition: .2s ease-in-out;
        position: fixed;
        top: 0;
        z-index: 500;
        clip-path: circle(0px at calc(100% - 40px) 20px);
    }

    .nav-container.active {
        background: var(--main-color);
        visibility: visible;
        clip-path: circle(80% at 50% 50%);


    }

    nav {
        display: flex;
        height: 100%;
        flex-direction: column;
        justify-content: center;
        align-items: flex-end;
        margin-right: 50px;
    }

  

    .nav-container nav div {
        margin: 10px 0;
        transition: .2s;
        transform: translateX(50px);

    }

     .nav-container.active nav div {
        transform: translateX(0px);
        
    }


    nav div a {
        color: var(--secondary-color);
        text-decoration: none;
        font-size: 40px;
        opacity: 0;
        transition: .2s;
        font-weight:700;

    }

    

    .nav-container.active nav div:hover {
        transform: skew(-10deg);
        text-decoration: underline;

    }

    .nav-container.active nav div a {
        opacity: 1;
        transform: translateX(0);
    } 

    @media(min-width: 600px){
        .nav-container {
            width: 650px;
            height: 650px;
            right: -125px;
            top: -75px;
            border-radius: 50%;
            clip-path: circle(0px at 100% 25%);
            position: absolute;

        }

        nav {
            margin-right: 200px;
        }
    }


</style>