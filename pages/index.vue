<template>
  <div>
    <h1 class="text-4xl">{{ page.title }}</h1>
    <h2 class="text-xl mb-8">{{ page.description}} </h2>
    <nuxt-content class="text-lg" :document="page"/>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    const slug = params.slug || "index";
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
      title: 'Home',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'This is my homepage'
        }
      ]
    }
  }
};
</script>
