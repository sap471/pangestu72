<template>
  <div
    class="lg:flex mx-4 md:mx-2 my-4 bg-gray-800 rounded shadow-md p-4 py-4 text-sm border-animation text-center lg:text-left"
  >
    <div class="lg:mr-auto my-auto">
      Copyright 2020 <span class="font-semibold">Estu Network</span>
    </div>
    <div class="lg:ml-auto lg:text-right">
      <!-- Footer Navigation -->
      <ul class="flex justify-center lg:justify-end">
        <li
          v-for="(item, index) in footer.navigation"
          :key="index"
          class="px-1 lg:border-r-2 border-gray-400"
        >
          <a class="font-semibold hover:text-blue-400" :href="item.slug">{{
            item.name
          }}</a>
        </li>
      </ul>
      <!-- Social Media Icons -->
      <span class="sosialmedia mt-4">
        <a :href="footer.social.facebook">
          <ion-icon style="background-color: #3b5999;" name="logo-facebook">
          </ion-icon>
        </a>
        <a :href="footer.social.instagram">
          <ion-icon style="background-color: #e4405f;" name="logo-instagram">
          </ion-icon>
        </a>
        <a :href="footer.social.twitter">
          <ion-icon style="background-color: #55acee;" name="logo-twitter">
          </ion-icon>
        </a>
        <a :href="footer.social.github">
          <ion-icon style="background-color: #24292e;" name="logo-github">
          </ion-icon>
        </a>
        <a href="#">
          <ion-icon
            style="background-color: #4fc08d;"
            name="logo-vue"
          ></ion-icon>
        </a>
        <a href="#">
          <ion-icon
            style="background-color: #2c251b;"
            name="logo-javascript"
          ></ion-icon>
        </a>
      </span>
    </div>
  </div>
</template>

<script>
import { footer } from "@/config";
export default {
  data: () => {
    return {
      footer,
    };
  },
};
</script>

<style>
.sosialmedia ion-icon {
  @apply rounded;
  font-size: 18px;
  padding: 4px;
  margin: 6px 4px;
  --ionicon-stroke-width: 20px;
}
</style>
