<template>
  <div class="mx-4 md:mx-2 lg:flex lg:flex-wrap">
    <!-- Loading -->
    <CenterNote
      v-if="isLoading"
      title="Loading ..."
      info="Sedang mengambil artikel"
    />
    <!-- Not Found -->
    <CenterNote v-else-if="notFound" />
    <!-- Content -->
    <div
      v-else
      class="w-full bg-gray-800 rounded overflow-hidden shadow-md pb-2 mb-3"
    >
      <div class="p-2 px-4">
        <h2 class="w-full text-3xl font-semibold hover:text-blue-300">
          <span>{{ post.title }}</span>
        </h2>
        <div class="text-xs text-gray-400">
          <span class="text-gray-100">{{ post.author }}</span> |
          {{
            post.date.updated
              ? new Date(post.date.updated).toLocaleString()
              : new Date(post.date.created).toLocaleString()
          }}
          |
          {{ post.comment ? post.comment + " Komentar" : "Tidak ada komentar" }}
        </div>
      </div>
      <div class="flex p-2 pr-4 pl-2">
        <div
          v-if="post.hasThumbnail"
          class="image h-64 rounded border border-animation mx-2"
        >
          <img
            :src="post.thumbnail.src"
            :alt="post.thumbnail.alt"
            class="object-contain h-full"
          />
        </div>
        <div class="text-md" :class="{ 'mx-2': !post.hasThumbnail }">
          <nuxt-content :document="post"></nuxt-content>
        </div>
      </div>
      <div class="text-xs px-4">
        <span class="text-gray-400">Category : </span>{{ post.category }}
        <span class="text-gray-400">Tags : </span>{{ post.tags }}
      </div>
    </div>
    <!-- End Content -->
  </div>
</template>

<script>
import CenterNote from "@/components/CenterNote";
export default {
  layout: "base",
  components: {
    CenterNote,
  },
  data: () => {
    return {
      isLoading: true,
      isPost: false,
      notFound: false,
      post: {
        title: "",
        description: "",
        summary: "",
        author: "",
        comment: false,
        date: {
          created: 0,
          updated: 0,
          published: 0,
        },
        hasThumbnail: false,
        thumbnail: {
          src: "",
          alt: "",
        },
        category: "",
        tags: "",
      },
    };
  },
  async beforeMount() {
    const slug = this.$route && this.$route.params && this.$route.params.slug;
    console.log(slug);
    const all = await this.$content("blog").fetch();
    console.log(all);
    try {
      const post = await this.$content("blog").limit(1).where({ slug }).fetch();
      const pages = await this.$content("pages")
        .limit(1)
        .where({ slug })
        .fetch();

      if (post.length) {
        this.isPost = true;
        this.post = post[0];
        console.warn(post);
      } else if (pages.length) {
        this.post = pages[0];
      } else {
        this.notFound = true;
      }
      this.isLoading = false;
    } catch (error) {}
  },
  head: {},
};
</script>

<style lang="postcss">
textarea {
  @apply bg-gray-700;
  @apply w-full;
}
</style>
