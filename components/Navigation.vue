<template>
  <div>
    <div class="nav-wrapper flex flex-col md:flex-row">
      <div class="flex">
        <nuxt-link
          class="w-full transition duration-500 ease-in-out hover:bg-blue-600 p-4"
          :to="{ path: '/' }"
        >
          <ion-icon name="home"></ion-icon>
          <span class="md:hidden">Home</span>
        </nuxt-link>
        <button
          type="button"
          class="md:hidden p-4 bg-blue-600"
          @click="isOpen = !isOpen"
        >
          <ion-icon name="arrow-down-outline"></ion-icon>
        </button>
      </div>
      <ul
        :class="{ hidden: !isOpen }"
        class="flex-none md:flex md:block navigation"
      >
        <li
          v-for="nav in navigation"
          :key="nav.name"
          class="transition duration-500 ease-in-out hover:bg-blue-600"
        >
          <div v-if="nav.dropdown" class="dropdown">
            <button class="dropdown-btn bg-transparent">
              {{ nav.name }}
            </button>
            <ul class="dropdown-menu md:absolute md:hidden text-gray-700 pt-4">
              <li v-for="item in nav.dropdown_menu" :key="item.name" class="">
                <nuxt-link
                  :to="{ path: item.link }"
                  class="bg-gray-200 hover:bg-gray-400 py-2 px-4 block whitespace-no-wrap"
                >
                  {{ item.name }}
                </nuxt-link>
              </li>
            </ul>
          </div>
          <nuxt-link v-else :to="{ path: nav.link }">
            {{ nav.name }}
          </nuxt-link>
        </li>
      </ul>
    </div>
    <div class="h-1 bg-blue-600" />
  </div>
</template>

<script>
import { navigation } from "~/config";
export default {
  data: () => {
    return {
      isOpen: false,
      navigation,
    };
  },
  computed: {},
};
</script>

<style>
.navigation {
  transition: all 0.5s ease-in-out;
  overflow: hidden;
}
.nav-wrapper button:focus {
  outline: none;
}
.dropdown:hover .dropdown-menu {
  display: block;
}
.dropdown-menu > button:focus {
  outline: none;
}
</style>
