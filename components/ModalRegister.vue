<template>
  <div id="modal-login" :class="shown? 'flex opacity-100' : 'hidden opacity-0'"
       class="bg-black bg-opacity-40 fixed w-screen h-screen inset-0 transition-opacity flex justify-center items-center"
       style="z-index: 2" @click.self="$emit('close')">
    <div class="bg-white rounded-xl w-[400px] p-6 flex flex-col">
      <h1 class="text-2xl font-semibold ">Регистрация</h1>
      <form class="pt-4 flex flex-col" @submit.prevent="register">
        <div class="mb-1">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="register-name">
            Имя
          </label>
          <input id="register-name" ref="name" class="textfield" type="text" placeholder="Сергей Сергеевич">
        </div>
        <div class="mb-1">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="register-password">
            Почта
          </label>
          <input id="register-email" ref="email" class="textfield" type="text" placeholder="example@mail.com">
        </div>
        <div class="mb-1">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="register-password">
            Пароль
          </label>
          <input id="register-password" ref="password" class="textfield" type="password" placeholder="*******">
        </div>
        <div class="mb-3">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="password-confirm">
            Повторите пароль
          </label>
          <input id="password-confirm" ref="passwordConfirm" class="textfield" type="password" placeholder="*******">
        </div>
        <div class="flex items-center justify-between">
          <button
            class="transition-colors bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
            type="submit">
            Зарегистрироваться
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalRegister",
  props: {
    shown: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    register() {
      const email = this.$refs.email.value
      const name = this.$refs.name.value
      const password = this.$refs.password.value
      const passwordConfirm = this.$refs.passwordConfirm.value

      this.$axios.$post("/auth/register", {
          email,
          name,
          password,
          password_confirmation: passwordConfirm
      }).then(() => {
        this.$auth.loginWith("laravelJWT", {
          data: {
            email,
            password
          }
        }).then(() => {
          window.location.reload()
        })
      }, (resp) => {
        console.log("fail")
        console.log(resp)
      })
    }
  }
}
</script>

<style scoped>

</style>
