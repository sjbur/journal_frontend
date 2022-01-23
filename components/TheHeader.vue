<template>
  <div class="p-6 border-b border-gray-200 flex justify-between sticky top-0 bg-body">
    <TheLogo/>

    <div class="flex items-center space-x-6">
      <IconSearch/>
      <IconBell/>
      <button class="btn-black" @click="$auth.loggedIn? $router.push({ path: '/add-post' }) : ''">Написать</button>

      <IconUser v-if="!$auth.loggedIn" @click="$nuxt.$emit('showLogin')"/>
      <img v-else width="35" height="35" class="cursor-pointer" src="/no-avatar.png" alt=""
           @click="$router.push({ path: '/profile' }) "/>
    </div>
  </div>
</template>

<script>
import IconSearch from "~/components/icons/IconSearch";
import IconBell from "~/components/icons/IconBell";
import IconUser from "~/components/icons/IconUser";

export default {
  name: "TheHeader",
  components: {IconBell, IconSearch, IconUser},
}
</script>

<style scoped>

</style>
