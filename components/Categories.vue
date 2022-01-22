<template>
  <div class="flex flex-col py-3 pl-0 m-2">
    <h3 class="font-semibold text-2xl pb-3 mr-20">Категории</h3>

    <CategoryItem v-for="(category, index) in categories" :key="index" class="pb-3" :value="category.name" />
  </div>
</template>

<script>
export default {
  name: "Categories",
  props: {
    categories: {
      type: Array,
      default: () => []
    }
  }
}
</script>

<style scoped>

</style>
