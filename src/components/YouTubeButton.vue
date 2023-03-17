<template>
  <a
    :href="href"
    target="_blank"
    class="text-center px-3 py-2 rounded border-2 border-red-600 bg-red-500 hover:bg-red-600 hover:text-white transition-colors hover:cursor-pointer"
  >
    <slot></slot>
  </a>
</template>

<script setup>

const props = defineProps({
    href: String
})

</script>