<template>
  <div class="flex w-full rounded text-center shadow-md h-48 bg-gray-800">
    <div class="w-full text-center my-auto">
      <div class="text-4xl font-bold">
        <span v-text="title"></span>
      </div>
      <p v-text="info"></p>
      <nuxt-link class="hover:text-blue-400" to="/">
        Kembali ke Beranda
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: "404 Not Found",
    },
    info: {
      type: String,
      default: null,
    },
  },
};
</script>

<style></style>
