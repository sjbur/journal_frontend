<template>
    <div class="border bg-white m-2 group border-[#ededed] hover:border-gray-500 overflow-hidden rounded-[15px]">
      <client-only>
        <a class="flex flex-col h-full" :href="`/${article.url}`">
          <img
            class="w-100 h-auto transition-opacity group-hover:opacity-75"
            :src="article.image"
            :alt="article.title" />

          <div class="flex space-x-2 p-4 pb-0">
            <a href="#" class="transition-opacity hover:opacity-50">{{ article.category }}</a>
            <div class="dot-before">
              {{ correctDate }}
            </div>
          </div>

          <div class="p-4 pt-1 pb-2">
            <h1 class="text-xl font-semibold">{{ article.title }}</h1>
          </div>

          <div class="flex flex-col justify-end px-4 pt-2 pb-4 h-full">
            <div class="flex space-x-2 items-center">
              <ArticleLike :article="article"/>
              <IconComment class="header-icon"/>
              <IconBookmark class="header-icon"/>
            </div>
          </div>
        </a>
      </client-only>
    </div>
</template>

<script>
import IconComment from "~/components/icons/IconComment";
import IconBookmark from "~/components/icons/IconBookmark";

export default {
  name: "CardArticle",
  components: {IconBookmark, IconComment},
  props: {
    article: {
      type: Object,
      default: () => {
      }
    }
  },
  computed: {
    correctDate() {
      if (!this.article.created_at)
        return

      const date = new Date(this.article.created_at)
      return ("0" + date.getDate()).slice(-2) + "." + ("0" + (date.getMonth() + 1)).slice(-2)
    },
  }
}
</script>

<style scoped>

</style>
