<template>
  <div
    class="header-brand mx-4 md:mx-2 mt-6 mb-4 rounded overflow-hidden shadow-md"
  >
    <div class="flex-none md:flex py-6">
      <div class="brand text-center md:text-left px-8 mr-auto">
        <h2 class="font-bold text-3xl">
          {{ blogSettings.blog_title }}
        </h2>
        <p>{{ blogSettings.blog_desc }}</p>
      </div>
      <div class="search p-4 pb-0 ml-auto my-auto">
        <form class="flex" action="#" method="get">
          <input
            id="search-input"
            type="text"
            name="search-input"
            class="rounded-l bg-white text-gray-900 py-2 px-4 block w-full appearance-none leading-normal"
            placeholder="Cari disini ..."
          />
          <button type="submit" class="rounded-r bg-blue-600 p-2">
            <ion-icon name="search"></ion-icon>
          </button>
        </form>
      </div>
    </div>
    <!-- Navigation Here -->
    <Navigation />
  </div>
</template>

<script>
import Navigation from "./Navigation";
import { settings } from "~/config";

export default {
  components: {
    Navigation,
  },
  data: () => {
    return {
      blogSettings: settings,
    };
  },
};
</script>

<style>
.header-brand {
  background: #2d3748 url("~assets/img/bgheader.png");
}
.navigation > li {
  padding: 0.75rem;
  font-weight: 700;
  /* text-transform: uppercase; */
}
ion-icon {
  font-size: 16px;
}
</style>
