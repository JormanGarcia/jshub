<template>
    <div class="container">
        <h1 class="search_title"  >{{$route.query.q}}'s Results</h1>

        <Posts :posts="posts" />
    </div>
</template>

<script>
export default {
    async asyncData($context){
        const {q} = $context.query;
        const posts = await fetch(`https://strapi-blog-jorman.herokuapp.com/posts?_where[_or][0][title_contains]=${q}&_where[_or][1][body_contains]=${q}`).then(res=>res.json());
    
        return {posts}
    }
}
</script>

<style>
.search_title {
    margin-bottom: 50px;
}
</style>