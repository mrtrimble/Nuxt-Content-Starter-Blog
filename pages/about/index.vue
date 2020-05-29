<template>
  <div>
    <h1 class="text-4xl mb-8">{{ page.title }}</h1>
    <nuxt-content :document="page"/>
  </div>
</template>

<script>
export default {
  layout: 'default',
  async asyncData({ $content, params, error }) {
    const slug = params.slug || "about/index";
    const page = await $content(slug)
      .fetch()
      .catch(err => {
        error({ statusCode: 404, message: "Page not found" });
      });

    return {
      page
    };
  },
  head(){
    return{
      title: 'About',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'This is my about page'
        }
      ]
    }
  }

};
</script>