<template>
  <div class="pt-10 px-6 w-7/12">
    <h1 class="font-bold text-6xl">Опубликовать свой текст</h1>

    <form @submit.prevent="sendArticle">
      <div class="py-6">
        <div class="flex flex-col mb-6">
          <p class="font-semibold">Заголовок</p>
          <input ref="title" type="text" class="textfield-add-post" placeholder="Как я накопил миллион рублей"/>
        </div>
        <div class="flex flex-col mb-6">
          <p class="font-semibold">Ссылка на изображение статьи</p>
          <input ref="image" type="text" class="textfield-add-post" placeholder=""/>
        </div>
        <div class="flex flex-col mb-6">
          <p class="font-semibold">Текст</p>
          <textarea ref="text" class="textfield-add-post h-48" placeholder="Как я накопил миллион рублей"/>
        </div>
        <div class="flex flex-col mb-6">
          <p class="font-semibold">Категория статьи</p>
          <input ref="category" type="text" class="textfield-add-post" placeholder=""/>
        </div>
        <input type="submit" class="btn-blue" value="Отправить статью" />
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "AddPost",
  beforeMount() {
    if (!this.$auth.loggedIn)
      this.$nuxt.error({statusCode: 404, message: "Not found"})
  },
  methods: {
    sendArticle() {
      this.$axios.$post("/articles/create", {
        title: this.$refs.title.value,
        text: this.$refs.text.value,
        category: this.$refs.category.value,
        image: this.$refs.image.value,
      }).then((resp) => {
        console.log(resp)
        this.$router.push({path: "/"})
      }, (resp) => {
        console.log(resp)
      })
    }
  }
}
</script>

<style scoped>

</style>
