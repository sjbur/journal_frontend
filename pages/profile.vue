<template>
<div class="w-screen h-screen flex flex-col justify-center items-center">
  <button class="btn-black" @click="$auth.logout()">Выйти</button>
</div>
</template>

<script>
export default {
  name: "Profile"
}
</script>

<style scoped>

</style>
