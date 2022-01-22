<template>
  <div
    class="
    flex
    items-center
    justify-center
    w-screen
    h-screen
    bg-gradient-to-r
    from-indigo-600
    to-blue-400
  "
  >
    <div class="px-40 py-20 bg-white rounded-md shadow-xl">
      <div class="flex flex-col items-center">
        <h1 class="font-bold text-blue-600 text-9xl">{{ error.statusCode }}</h1>

        <p class="mb-8 text-center text-gray-500 md:text-lg">
          {{ error.message }}
        </p>

        <a
          href="#"
          class="px-6 py-2 text-sm font-semibold text-blue-800 bg-blue-100"
        >На главную</a
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Error",
  props: {
    error: {
      type: Object,
      default: () => {},
    },
  },
}
</script>

<style scoped>

</style>
