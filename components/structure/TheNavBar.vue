<template>
  <header class="h-16 bg-indigo-600">
    <div class="container mx-auto flex justify-between h-full">
      <section id="logo" class="flex items-center justify-center h-full">
        <h1 class="text-3xl text-white uppercase">My Website</h1>
      </section>
      <nav class="h-full">
        <ul class="flex items-center justify-center h-full">
          <li><nuxt-link class="text-indigo-100 hover:text-white uppercase px-4" to="/">Home</nuxt-link></li>
          <li><nuxt-link class="text-indigo-100 hover:text-white uppercase px-4" to="/about">About</nuxt-link></li>
          <li><nuxt-link class="text-indigo-100 hover:text-white uppercase px-4" to="/posts">Blog</nuxt-link></li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<style lang="scss" scoped>
</style>