<script setup>
const props = defineProps({
  title: String,
  description: String,
  image: String,
  imageAlt: String,
  buttons: Array
});
</script>

<template>
  <div class="flex flex-col gap-12 mt-12 mb-24 lg:items-center lg:flex-row">
    <div class="flex-1 w-full">
      <NuxtImg
        v-if="image"
        :src="image"
        :alt="imageAlt"
        sizes="100vw lg:600px"
        class="rounded-2xl shadow-lg w-full object-cover"
      />
    </div>
    <div class="flex-1 w-full">
      <h1 v-if="title" class="text-4xl font-bold text-zinc-800 sm:text-5xl mb-4">
        {{ title }}
      </h1>
      <p v-if="description" class="max-w-xl text-lg text-zinc-600 sm:text-xl mb-6">
        {{ description }}
      </p>
      <div class="flex flex-wrap gap-4 mt-6">
        <div v-for="button in buttons" :key="button.label + button.url">
          <NuxtLink
            v-if="button.label && button.url"
            :href="button.url"
            class="inline-flex px-6 py-3 text-white bg-green-600 rounded-xl font-semibold shadow transition-colors duration-300 hover:bg-green-700"
          >
            {{ button.label }}
          </NuxtLink>
        </div>
      </div>
    </div>
  </div>
</template>
