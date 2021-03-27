<template>
<div class="container">

    <Posts :posts="posts" />
    
</div>
</template>

<script>
export default {
  methods: {
  },

    async asyncData(){
        const posts = await fetch('https://strapi-blog-jorman.herokuapp.com/posts').then(res=> res.json())

        console.log(posts)
        return {posts}
    }
}
</script>

<style scoped>
  .v-lazy-image {
    filter: blur(10px);
    transition: filter 0.7s;
  }
  .v-lazy-image-loaded {
    filter: blur(0);
  }
</style>