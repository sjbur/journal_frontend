<template>
  <div class="flex space-x-1.5 items-center header-icon" @click="like">
    <IconLikeFilled v-if="likesCount"/>
    <IconLike v-else />
    <span>{{ likesCount }}</span>
  </div>

</template>

<script>
import IconLike from "~/components/icons/IconLike";
import IconLikeFilled from "~/components/icons/IconLikeFilled";

export default {
  name: "ArticleLike",
  components: {
    IconLike, IconLikeFilled
  },
  props: {
    article: {
      type: Object,
      default: () => {
      }
    }
  },
  data() {
    return {
      updatedLikes: null,
    }
  },
  computed: {
    likesCount() {
      if (this.updatedLikes)
        return this.updatedLikes

      return this.article.likes || 0
    }
  },
  methods: {
    like() {
      if (!this.$auth.loggedIn) {
        this.$emit('loggedOut')
        return
      }

      this.$axios.$post(`/articles/${this.article.id}/like`).then((resp) => {
       this.updatedLikes = resp.likes
        this.$forceUpdate();
      })
    }
  }

}
</script>

<style scoped>

</style>
