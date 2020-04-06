<template>
  <div class="background">
    <div class="container">
      <div class="blog_body">
        <!-- <logo /> -->
        <span class="title-dark" v-html="post.title"></span>
        <img class="cover-image" :src="post.cover_img" />
        <div class="blog_content" v-html="post.entry_body"></div>
      </div>
    </div>
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
.container {
  margin: 0 auto;
  display: block;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.cover-image {
  width: 100%;
  max-height: 600px;
  object-fit: cover;
  margin-top: 15px;
  margin-bottom: 15px;
  border-radius: 4px;
}
.links {
  padding-top: 15px;
}
.blog_body {
  padding-bottom: 5vh;
  padding-top: 5vh;
}
.blog_content {
  text-align: left;
  max-width: 100%;
  overflow: hidden;
  font-size: 18px;
}
.blog_content >>> img {
  width: 100%;
  max-height: 600px;
  object-fit: cover;
  text-align: center;
}
</style>
