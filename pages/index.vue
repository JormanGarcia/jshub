<template>
  <div class="container">
    <Hero :posts="posts" />
  </div>
</template>
<script>
export default {
    asyncData: async function(){
        const posts = await fetch('https://strapi-blog-jorman.herokuapp.com/posts/?_limit=3').then(res=>res.json());
        return { posts }
    }
}
</script>

<style>

</style>
