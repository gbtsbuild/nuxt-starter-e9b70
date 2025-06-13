<script setup>
const props = defineProps({
  title: String,
  icons: Array
});
</script>

<template>
  <div class="mb-20">
    <h2 class="text-2xl font-bold text-center text-green-700 mb-10" v-if="title">{{ title }}</h2>
    <div class="flex flex-wrap items-center justify-center gap-x-12 gap-y-8 sm:gap-x-24 sm:gap-y-12">
      <div v-for="icon in icons" :key="icon.name" class="flex items-center justify-center">
        <Icon
          v-if="icon.name"
          :name="icon.name"
          class="h-12 w-12 text-green-500 transition-transform duration-200 hover:scale-110"
        />
      </div>
    </div>
  </div>
</template>
