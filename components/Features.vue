<script setup>
const props = defineProps({
  title: String,
  description: String,
  items: Array,
});
</script>

<template>
  <h2
    class="text-3xl font-bold text-center text-green-700 sm:text-4xl"
    v-if="title"
  >
    {{ title }}
  </h2>
  <p
    class="max-w-3xl mx-auto mt-4 text-lg text-center text-zinc-600"
    v-if="description"
  >
    {{ description }}
  </p>
  <div class="grid gap-8 mt-10 mb-20 md:grid-cols-2">
    <div
      v-for="item in items"
      :key="item.title"
      class="p-8 border-2 border-green-200 border-dashed rounded-xl bg-white shadow-sm hover:shadow-lg transition-shadow duration-200 sm:p-12"
    >
      <h3 class="text-2xl font-semibold text-green-700 flex items-center gap-2" v-if="item.title">
        <span v-if="item.icon" class="text-3xl">{{ item.icon }}</span>
        {{ item.title }}
      </h3>
      <p class="mt-2 leading-relaxed text-zinc-500" v-if="item.description">
        {{ item.description }}
      </p>
    </div>
  </div>
</template>
