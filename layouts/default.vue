<template>
<div>
  <TheHeader />
  <Nuxt />
  <ModalLogin :shown="showLogin" @close="toggleLoginModal" />
</div>
</template>

<script>
export default {
  name: "Default",
  data() {
    return {
      showLogin: false
    }
  },
  created() {
    this.$nuxt.$on('showLogin', () => this.toggleLoginModal())
  },
  methods: {
    toggleLoginModal() {
      this.showLogin = !this.showLogin
    }
  }
}
</script>

<style scoped>

</style>
