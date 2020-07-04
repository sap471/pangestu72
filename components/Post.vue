<template>
  <div class="bg-gray-800 rounded overflow-hidden shadow-md pb-2 mb-3">
    <div class="p-2 px-4">
      <h2 class="text-2xl font-semibold">
        <!-- <a class="hover:text-blue-300" :href="post.slug">
          {{ post.title }}
        </a> -->
        <nuxt-link :to="{ path: post.slug }" v-text="post.title"></nuxt-link>
      </h2>
      <div class="text-xs text-gray-400">
        By <span class="text-gray-100">{{ post.author }}</span> |
        <!-- {{
          post.date.modified !== null
            ? new Date(post.date.modified).toLocaleString()
            : new Date(post.date.created).toLocaleString()
        }} -->
        |
        {{ post.comment ? post.comment + " Komentar" : "Tidak ada komentar" }}
      </div>
    </div>
    <div class="flex p-2 pr-4 pl-2">
      <div
        v-if="post.hasThumbnail"
        class="image h-32 w-32 rounded border border-animation mx-2"
      >
        <img
          :src="post.thumbnail.src"
          :alt="post.thumbnail.alt"
          class="object-contain h-full"
        />
      </div>
      <div class="" :class="{ 'mx-2': !post.hasThumbnail }">
        {{ post.summary }}
      </div>
    </div>
    <div class="text-xs px-4">
      <span class="text-gray-400">Category : </span>{{ post.category }}
      <span class="text-gray-400">Tags : </span>{{ post.tags }}
    </div>
  </div>
</template>

<script>
import { categories } from "@/config";

export default {
  props: {
    post: {
      type: Object,
      default: null,
    },
  },
  date: () => {
    return {
      categories,
    };
  },
};
</script>

<style></style>
