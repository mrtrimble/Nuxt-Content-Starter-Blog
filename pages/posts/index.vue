<template>
<section class="text-gray-700 body-font overflow-hidden">
  <div class="container px-5 py-24 mx-auto">
    <div class="-my-8">
      <!-- {{posts}} -->
      <div v-for="(post, index) in posts" :key="index" class="py-8 flex flex-wrap md:flex-no-wrap">
        <div class="md:w-64 md:mb-0 mb-6 flex-shrink-0 flex flex-col">
          <span class="tracking-widest font-medium title-font text-gray-900 uppercase">{{post.category}}</span>
          <span class="mt-1 text-gray-500 text-sm">{{post.updatedAt}}</span>
        </div>
        <div class="md:flex-grow">
          <h2 class="text-2xl font-medium text-gray-900 title-font mb-2">
            {{ post.title }}
          </h2>
          <p class="leading-relaxed">
            {{ post.summary }}
          </p>
          <nuxt-link :to="{name: 'posts-slug', params: { slug: post.slug } }" class="text-green-500 inline-flex items-center mt-4">Learn More
            <svg class="w-4 h-4 ml-2" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round">
              <path d="M5 12h14"></path>
              <path d="M12 5l7 7-7 7"></path>
            </svg>
          </nuxt-link>
        </div>
      </div>
    </div>
  </div>
</section>
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