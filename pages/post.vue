<template>
    <div>
        

        <img class="poster" :src="`https://strapi-blog-jorman.herokuapp.com${post.image.formats.medium.url}`" />
        <div class="container">
            <div class="title_container">
                <div class="post_title">{{post.title}}</div>
            </div>
            <p class="date">{{new Date(post.published_at).toString().slice(0, 15)}}</p>
            <div class="post_body" v-html="$md.render(post.body)"></div>
        </div>

        
    </div>
</template>

<script>
export default {
  
    

    async asyncData($context){
        const post = await fetch(`https://strapi-blog-jorman.herokuapp.com/posts/${$context.route.query.id}`).then(res=>res.json())
        console.log(post)
        return {post}
    },
}

</script>

<style>


.date {
    margin-bottom: 20px;
    font-weight: 400;
    margin-left: auto;
    font-size: 15px;
    text-align: right;
    opacity: .5;

}
.poster {
    width: 100%;
    margin: 100px auto -70px;
    max-height: 350px;
    object-fit: cover;
}



.title_container {
    display: flex;
    justify-content: center;
    margin-bottom: 40px;
}

.post_title {
    font-size: 40px;
    text-align: center;
    font-weight: 700;
    position: relative;
    z-index: 0;
    display: inline-block;
    margin: auto;
}

.post_title::before{
    width: 50%;
    height: 5px;
    background: var(--main-color);
    content: "";
    position: absolute;
    bottom: -20px;
    right: 0;
    left: 0;
    margin: auto;
    border-radius: 10px;
}

.post_body a {
    opacity: .5;
}

.post_body a:hover {
    opacity: 1;
    text-decoration: underline;
    font-weight: 600;
    color: var(--main-color);
}

.post_body p {
    margin-bottom: 25px;
}


.post_body p:last-of-type{
    margin-bottom: 0;
}


@media(min-width: 700px){
    .poster {
        width: 90%;
        display: block;
        border-radius: 10px;
    }

    .post_body {
        padding: 30px 0 30px 50px;
        border-left: 2px solid var(--main-color);
    }

   
}
</style>