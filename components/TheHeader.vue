<template>
  <div class="p-6 border-b border-gray-200 flex justify-between">
    <TheLogo/>

    <div class="flex items-center space-x-6">
      <IconSearch />
      <IconBell />
      <button class="btn-black">Написать</button>
      <IconUser />
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
