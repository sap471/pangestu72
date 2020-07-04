<template>
  <!-- Box -->
  <div class="box rounded overflow-hidden shadow-md">
    <div class="box-title bg-blue-600 p-2 px-5">
      <span class="font-semibold" style="font-size: 1.25rem;">
        {{ $attrs.title }}
      </span>
    </div>
    <div class="box-content bg-gray-800 p-2 px-4 text-sm pb-4">
      <slot></slot>
    </div>
  </div>
  <!-- End Box -->
</template>

<script>
export default {};
</script>

<style></style>
