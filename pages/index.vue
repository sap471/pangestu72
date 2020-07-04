<template>
  <div class="mx-4 md:mx-2 lg:flex lg:flex-wrap">
    <!-- Content Wrapper -->
    <div class="w-full lg:w-2/3 flex-row lg:pr-2">
      <div v-for="item in posts" :key="item.path">
        <Post :post="item" />
      </div>
    </div>
    <!-- End Content Wrapper -->
    <!-- Sidebar Wrapper -->
    <div class="w-full lg:w-1/3 lg:pl-2">
      <SidebarBox title="Postingan Terakhir">
        <ul>
          <li
            v-for="(item, index) in posts"
            :key="index"
            class="truncate pt-1 border-b-2 border-gray-600"
          >
            <a class="hover:text-blue-300" :href="item.path">
              {{ item.title }}
            </a>
          </li>
        </ul>
      </SidebarBox>
    </div>
  </div>
</template>

<script>
import Post from "@/components/Post";
import SidebarBox from "@/components/SidebarBox";

export default {
  layout: "base",
  components: {
    Post,
    SidebarBox,
  },
  async asyncData({ $content }) {
    const posts = await $content("blog")
      .limit(5)
      .where({ published: true })
      .fetch();

    return { posts };
  },
  data: () => {
    return {
      last: [
        {
          content: "Abang bakso bawa walkie talkie, kijang satu ganti!",
        },
        {
          content: "Apa yang harus dilakukan jika terlalu lama sendiri ?",
        },
        {
          content: "Tang Tang Dung Dung Des",
        },
        {
          content: "Laptop Murah 100rban, tapi hanya dalam mimpi",
        },
      ],
    };
  },
};
</script>

<style></style>
