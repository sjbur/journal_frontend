<template>
<div>
  <TheHeader />
  <Nuxt />
  <ModalLogin :shown="showLogin" @close="toggleLoginModal" />
  <ModalRegister :shown="showRegister" @close="showRegister = false" />
</div>
</template>

<script>
export default {
  name: "Default",
  data() {
    return {
      showLogin: false,
      showRegister: false
    }
  },
  created() {
    this.$nuxt.$on('showLogin', () => this.toggleLoginModal())
    this.$nuxt.$on('showRegister', () => this.showRegisterModal())
  },
  methods: {
    toggleLoginModal() {
      this.showLogin = !this.showLogin
    },

    showRegisterModal() {
      this.showLogin = false
      this.showRegister = true
    }
  }
}
</script>

<style scoped>

</style>
