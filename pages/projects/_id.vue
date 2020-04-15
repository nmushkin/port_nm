<template>
  <div class="blog_body">
    <!-- <logo /> -->
    <img class="cover-image" :src="post.cover_img" />
    <span class="title-dark" v-html="post.title"></span>
    <div class="blog_content" v-html="post.entry_body"></div>
  </div>
</template>

<script>
export default {
  name: 'ProjectPost',
  async asyncData(context) {
    const linkResolver = function(doc) {
      // Pretty URLs for known types
      if (doc.type === 'blog_post') return '/projects/' + doc.uid
      if (doc.type === 'page') return '/' + doc.uid
      // Fallback for other types, in case new custom types get created
      return '/doc/' + doc.id
    }
    const Prismic = require('prismic-javascript')
    const PrismicDOM = require('prismic-dom')
    const apiEndpoint = 'https://nmushkinblog.cdn.prismic.io/api/v2'
    const api = await Prismic.getApi(apiEndpoint)
    const response = await api.getByUID('blog_post', context.params.id)
    const blogPost = {
      title: PrismicDOM.RichText.asHtml(response.data.title, linkResolver),
      cover_img: response.data.cover_img_link.url,
      entry: response.data.content[0],
      entry_body: PrismicDOM.RichText.asHtml(
        response.data.content,
        linkResolver
      )
    }
    return {
      post: blogPost
    }
  },
  created() {
    console.log(this.post)
  }
}
</script>

<style scoped>
.cover-image {
  width: 100%;
  max-height: 400px;
  object-fit: cover;
  border-bottom: 1px solid #000000;
}
.links {
  padding-top: 15px;
}
.title-dark {
  margin-top: 20px;
  margin-bottom: 20px;
}
.blog_body {
  padding-bottom: 5vh;
  width: 100%;
  display: inline-flex;
  flex-direction: column;
  text-align: center;
  align-items: center;
  justify-content: center;
}
.blog_content {
  text-align: left;
  max-width: 800px;
  font-size: 18px;
  width: 95%;
}
.blog_content >>> img {
  width: 100%;
  max-height: 600px;
  object-fit: cover;
  text-align: center;
}
</style>
