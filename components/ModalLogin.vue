<template>
  <div id="modal-login" :class="shown? 'flex opacity-100' : 'hidden opacity-0'" class="bg-black bg-opacity-40 fixed w-screen h-screen inset-0 transition-opacity flex justify-center items-center"
       style="z-index: 2" @click.self="$emit('close')">
    <div class="bg-white rounded-xl w-[400px] p-6 flex flex-col">
      <h1 class="text-2xl font-semibold ">Войдите в Журнал</h1>
      <p class="pt-3">
        Вы сможете комментировать статьи, ставить лайки и добавлять выбранные статьи в избранное
      </p>

      <form class="pt-3 flex flex-col" @submit.prevent="login">
        <div class="mb-4">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="email">
            Почта
          </label>
          <input id="email" ref="email" class="textfield" type="text" placeholder="example@mail.com">
        </div>
        <div class="mb-6">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="password">
            Пароль
          </label>
          <input id="password" ref="password" class="textfield" type="password" placeholder="*******">
        </div>
        <div class="flex items-center justify-between">
          <button
            class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
            type="submit">
            Войти
          </button>
          <a class="inline-block align-baseline font-bold text-sm text-blue-500 hover:text-blue-800" href="#">
            Забыли пароль?
          </a>
        </div>

        <div class="mt-5 p-3 w-full transition-colors bg-gray-50 hover:bg-gray-100 rounded cursor-pointer">
          <a class="text-blue-500 flex justify-center" href="/register">Создать аккаунт</a>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalLogin",
  props: {
    shown: {
      type: Boolean,
      default: false
    }
  },
  mounted() {

  },
  methods: {
    login() {
      const email = this.$refs.email.value
      const password = this.$refs.password.value

      this.$auth.loginWith("laravelJWT", {data: {email, password} }).then(() => {
        window.location.reload()
      }, () => {
        // console.log("fail")
        // console.log(resp)
      })
    },
  }
}
</script>

<style lang="scss" scoped>

</style>
