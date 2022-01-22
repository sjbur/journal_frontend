<template>
  <div class="body p-6 flex flex-col md:flex-row">
    <Categories :categories="categories" />

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3">
      <CardArticle v-for="(article, index) in articles" :key="index" :article="article" />
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    let articlesResponse
    let categoriesResponse

    try {
      await $axios.$get("/articles/").then((resp) => {
        articlesResponse = resp
      })

      await $axios.$get("/categories/").then((resp) => {
        categoriesResponse = resp
      })
    }

    catch(ex) {

    }

    return {
      articles: articlesResponse,
      categories: categoriesResponse
    }

  },
}
</script>

<style>
@import "~/assets/index.css";
</style>
