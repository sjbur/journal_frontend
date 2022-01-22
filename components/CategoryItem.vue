<template>
<div class="transition-colors hover:bg-white rounded p-3 cursor-pointer">
  {{ value }}
</div>
</template>

<script>
export default {
  name: "CategoryItem",
  props: {
    value: {
      type: String,
      default: ""
    }
  }
}
</script>

<style scoped>

</style>
