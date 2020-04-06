<template>
  <div class="post-container">
    <h1>{{ response }}</h1>
    <div
      v-for="(post, index) in prismPosts"
      :key="post.title + '_' + index"
      class="post_thumb"
      :style="{ backgroundImage: `url(${post.cover})` }"
    >
      <nuxt-link :to="'/projects/' + post.id">
        <div class="post_thumb_in">
          <!-- <router-link :to="'/blog/' + post.slug"> -->
          <h2>{{ post.title }}</h2>
          <p>{{ post.content }}</p>
          <!-- <img class="cover-image" :src="'http://localhost:1337' + post.cover" /> -->
          <!-- <nuxt-link :to="'/projects/' + post.id">View</nuxt-link> -->
          <!-- </router-link> -->
        </div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
const Prismic = require('prismic-javascript')
// const PrismicDOM = require('prismic-dom')
const apiEndpoint = 'https://nmushkinblog.cdn.prismic.io/api/v2'
export default {
  async asyncData() {
    // const prismPosts = []
    const api = await Prismic.getApi(apiEndpoint)
    const response = await api.query('')
    return { response }
    // let entry = 0
    // for (entry in response.results) {
    //   const post = response.results[entry]
    //   prismPosts.push({
    //     id: post.uid,
    //     title: post.data.title[0].text,
    //     content: post.data.summary_text,
    //     cover: post.data.cover_img_link.url
    //   })
    // }
    // return { prismPosts }
  },
  data() {
    return { posts: [] }
  }
}
</script>

<style scoped>
.post-container {
  /* background-color: #aaaaaa; */
  margin-top: 5vh;
}
.post_thumb {
  padding: 10px;
  height: 30vh;
  background-size: cover;
  background: no-repeat center;
  border-radius: 2px;
  margin-top: 15px;
  margin-bottom: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.cover-image {
  width: 50%;
}
.post_thumb_in {
  background-color: rgba(50, 50, 50, 0.9);
  padding: 10px;
  border-radius: 4px;
}
.post_thumb_in:hover {
  border: 2px solid #ffffff;
}
h2 {
  color: #eeeeee;
}
p {
  color: #dddddd;
}
</style>
