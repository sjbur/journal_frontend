<template>
  <div class="body p-6">
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3">
      <CardArticle v-for="(article, index) in articles" :key="index" :article="article" />
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    let response

    try {
      await $axios.$get("/articles/").then((resp) => {
        response = resp
      })
    }

    catch(ex) {

    }

    return {
      articles: response
    }

  },
}
</script>

<style>
@import "~/assets/index.css";
</style>
