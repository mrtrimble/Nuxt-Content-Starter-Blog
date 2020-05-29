<template>
  <section class="text-gray-700 body-font overflow-hidden">
    <div class="container px-5 pb-24 mx-auto">
      <div class="flex flex-wrap -m-12">
        <div class="p-12 md:w-2/3 flex flex-col items-start">
          <span
            class="inline-block py-1 px-3 rounded bg-green-100 text-green-500 text-sm font-medium tracking-widest uppercase"
          >{{page.category}}</span>
          <h2
            class="sm:text-3xl text-2xl title-font font-medium text-gray-900 mt-4 mb-4"
          >{{ page.title }}</h2>
          <div class="markdown leading-relaxed mb-8" v-html="body"></div>
          <div
            class="flex items-center flex-wrap pb-4 mb-4 border-b-2 border-gray-200 mt-auto w-full"
          >
          </div>
          <a class="inline-flex items-center">
            <img
              alt="blog"
              src="https://dummyimage.com/104x104"
              class="w-12 h-12 rounded-full flex-shrink-0 object-cover object-center"
            />
            <span class="flex-grow flex flex-col pl-4">
              <span class="title-font font-medium text-gray-900 uppercase">{{page.author}}</span>
              <span class="text-gray-500 text-sm">UI DEVELOPER</span>
            </span>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import marked from "marked";

export default {
  async asyncData({ $content, params, error }) {
    const page = await $content("posts", params.slug)
      .fetch()
      .catch(err => {
        error({ statusCode: 404, message: "Page not found" });
      });

    return {
      page
    };
  },
  computed:{
    body(){
      return marked(this.page.body)
    }
  },
  head() {
    return {
      title: this.page.title,
      meta: [
        {
          hid: "description",
          name: "description",
          content: this.page.summary
        }
      ]
    };
  }
};
</script>

<style lang="scss">
.markdown {
  @apply leading-relaxed text-lg;
}
/* Headers */
.markdown h1,
.markdown h2 {
  @apply text-2xl my-6 font-bold;
}
.markdown h3,
.markdown h4,
.markdown h5,
.markdown h6 {
  @apply text-xl my-3 font-semibold;
}
/* Links */
.markdown a {
  @apply text-blue-600;
}
.markdown a:hover {
  @apply underline;
}
/* Paragraph */
.markdown p {
  @apply mb-4;
}
/* Lists */
.markdown ul,
.markdown ol {
  @apply mb-4 ml-8;
}
.markdown li > p,
.markdown li > ul,
.markdown li > ol {
  @apply mb-0;
}
.markdown ol {
  @apply list-decimal;
}
.markdown ul {
  @apply list-disc;
}
/* Blockquotes */
.markdown blockquote {
  @apply p-0 p-2 mx-6 bg-gray-100 mb-4 border-l-4 border-gray-400 italic;
}
.markdown blockquote > p {
  @apply mb-0;
}
/* Tables */
.markdown td,
.markdown th {
  @apply px-2 py-1 border border-gray-400;
}
.markdown tr:nth-child(odd) {
  @apply bg-gray-100;
}
.markdown table {
  @apply mb-6;
}
</style>