<template>
  <div>
    <h1 class="text-4xl mb-8">Latest Updates</h1>
    <nuxt-link
      v-for="post in posts"
      :key="post.id"
      :to="{name: 'posts-slug', params: { slug: post.slug } }"
    >
      <div class="hover:bg-gray-200 px-4 py-2">
        <h2 class="text-2xl">{{post.title}}</h2>
        <p>{{ post.summary }}</p>
      </div>
    </nuxt-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: ["post"]
    };
  },
  async fetch() {
    this.posts = await this.$content("posts").fetch();
  },
  head(){
    return{
      title: 'Blog',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'This is my blog!'
        }
      ]
    }
  }
};
</script>

<style lang="scss" scoped>
</style>