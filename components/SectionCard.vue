<template>
  <section class="section-card flex flex-col md:flex-row items-center my-8 p-6 bg-white rounded-lg shadow">
    <img
      :src="section.image"
      :alt="section.title"
      class="w-full md:w-1/3 rounded mb-4 md:mb-0 md:mr-8 object-cover"
    />
    <div class="flex-1">
      <h2 class="text-2xl font-bold mb-2">{{ section.title }}</h2>
      <h3 class="text-lg text-gray-600 mb-2" v-if="section.subtitle">{{ section.subtitle }}</h3>
      <p class="mb-4">{{ section.description }}</p>
      <a
        v-if="section.cta"
        :href="section.cta.url"
        class="inline-block bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700 transition"
      >
        {{ section.cta.label }}
      </a>
    </div>
  </section>
</template>

<script setup>
defineProps({
  section: {
    type: Object,
    required: true
  }
});
</script>

<style scoped>
.section-card img {
  max-height: 220px;
}
</style>
