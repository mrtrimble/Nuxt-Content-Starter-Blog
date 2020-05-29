<template>
  <div>
    <TheHero 
      :heroHeadline="page.hero_headline"
      :heroText="page.hero_text"
      :linkOneText="page.link_one_text"
      :linkTwoText="page.link_two_text"
      :linkOneUrl="page.link_one_url"
      :linkTwoUrl="page.link_two_url"
      />
    <nuxt-content class="text-lg" :document="page"/>
  </div>
</template>

<script>
export default {
  layout: 'default',
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
      ],
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    }
  }
};
</script>
