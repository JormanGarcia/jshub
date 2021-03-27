<template>
<div class="posts-grid" >

        <div class="post" v-for="(post, key) in posts" :key="key" >
            <nuxt-link :to="`/post?id=${post.id}`" >
                <img :src="`https://strapi-blog-jorman.herokuapp.com${post.image.formats.small.url}`"  alt=" " />

                <div class="body">

                    <div class="title" >{{post.title}}</div> 
   

                </div>
            </nuxt-link>
        </div>

</div>  
    
</template>

<script>
export default {
   
    props: {
        posts: Array
    }
}
</script>


<style scoped>
    .posts-grid {
        display: grid;
        gap: 50px
    }

    .post {
        background: white;
        border-radius: 10px;
        overflow: hidden;
        border: 1px solid #ccc;
        box-shadow: 0 0 5px rgba(0, 0, 0, 0.0), inset 0 0 0 var(--main-color);
        transition: .2s;
    }

  

    .post:hover {
        box-shadow: 0px 3px 10px rgba(13, 42, 75, 0.1), inset 600px 0 0 var(--main-color);
        
    }

    .post img {
        width: 100%;
        height: 180px;
        object-fit: cover;
        border-bottom-right-radius: 20px;     
    }

    .body {
        padding: 20px;
    }

    .title {
        font-weight: 600;
        font-size: 20px;
        max-width: 100%;
        color: rgba(0, 0, 0, 0.6);
        height: 40px;
        line-height: 20px;
        -webkit-line-clamp: 2;
        -webkit-box-orient: vertical;
        overflow: hidden;
        text-overflow: ellipsis;
        display: block;
        display: -webkit-box;
    }

    .body-resume h1 {
        font-size: 16px;
    }

    @media(min-width: 700px){
        .posts-grid{
            grid-template-columns: 1fr 1fr;
            gap: 20px
        }
    }




</style>