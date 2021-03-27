<template>
  <div class="hero-container">
    <nuxt-link :to="`/post?id=${posts[0].id}`">
      <div class="hero">
        <img
          :src="`https://strapi-blog-jorman.herokuapp.com${posts[0].image.formats.medium.url}`"
        />

        <div class="overlay"></div>
        <div class="hero_title">{{ posts[0].title }}</div>
      </div>
    </nuxt-link>

    <div class="hero_posts">
      <div class="hero_post" v-for="(post, key) in posts.slice(1)" :key="key">
        <nuxt-link :to="`/post?id=${post.id}`">
          <img
            :src="`https://strapi-blog-jorman.herokuapp.com${post.image.formats.small.url}`"
            alt=" "
          />

          <div class="hero_post_body">
            <div class="hero_body_title">{{ post.title }}</div>

           
          </div>
        </nuxt-link>
      </div>
    </div>

    <div></div>
  </div>
</template>

<script>
export default {
  props: {
    posts: Array
  }
};
</script>

<style>
.hero-container {
  display: grid;
  gap: 20px;
}

.overlay {
  background: rgba(0, 0, 0, 0.4);
  height: 100%;
  width: 100%;
  position: absolute;
  top: 0;
}

.hero_title {
    position: absolute;
    top: 0;
    bottom: 0;
    display: flex;
    align-items: center;
    margin: auto;
    text-align: center;
    color:white;
    font-size: 25px;
    font-weight: 700;
    z-index: 200;
}

.hero {
  height: calc(100vh - 105px);
  border-radius: 10px;
  position: relative;
  overflow: hidden;
}

.hero img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.hero_posts {
  display: grid;
  grid-template-rows: 1fr 1fr;
  gap: 20px;
}

.hero_post {
  height: 330px;
  overflow: hidden;
  border-radius: 10px;
  background: white;
  border: 1px solid #ccc;
}

.hero_post img {
  height: 200px;
  width: 100%;
  object-fit: cover;
}

.hero_post_body {

  padding: 25px 20px;
}

.hero_body_title {
  font-size: 20px;
  font-weight: 700;

     
}

.hero_body_resume {
  max-width: 100%;
  color: rgba(0, 0, 0, 0.6);
  height: 60px;
  line-height: 20px;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
  display: block;
  display: -webkit-box;
}

@media (min-width: 800px) {
  .hero-container {
    grid-template-columns: 350px 1fr;
  }

  .hero_posts {
    display: grid;
    height: calc(100vh - 105px);
    grid-template-rows: 1fr 1fr;
    gap: 10px;
  }

  .hero_post {
    height: 100%;
  }

  @media (min-width: 900px) {
    .hero-container {
      grid-template-columns: 450px 1fr;
    }
  }
}
</style>
