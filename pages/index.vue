<template>
  <div>
    <!-- Hero Section -->
    <section v-if="content.hero" class="text-center py-12 bg-gray-100">
      <img :src="content.hero.image" :alt="content.hero.imageAlt" class="mx-auto mb-6 max-h-56" />
      <h1 class="text-3xl font-bold mb-2">{{ content.hero.title }}</h1>
      <p class="mb-4">{{ content.hero.description }}</p>
      <div>
        <a
          v-for="(btn, idx) in content.hero.buttons"
          :key="idx"
          :href="btn.url"
          class="inline-block bg-blue-600 text-white px-4 py-2 rounded mx-2 hover:bg-blue-700 transition"
        >
          {{ btn.label }}
        </a>
      </div>
    </section>

    <!-- Features Section -->
    <section v-if="content.features" class="py-10">
      <h2 class="text-2xl font-bold text-center mb-2">{{ content.features.title }}</h2>
      <p class="text-center mb-6">{{ content.features.description }}</p>
      <div class="flex flex-col md:flex-row justify-center gap-6">
        <div
          v-for="(item, idx) in content.features.items"
          :key="idx"
          class="bg-white shadow p-6 rounded-lg flex-1"
        >
          <h3 class="font-semibold text-xl mb-2">{{ item.title }}</h3>
          <p>{{ item.description }}</p>
        </div>
      </div>
    </section>

    <!-- Dynamic Product/Service Sections -->
    <div v-if="content.sections && content.sections.length">
      <SectionCard
        v-for="(section, idx) in content.sections"
        :key="idx"
        :section="section"
      />
    </div>

    <!-- Blog Excerpts -->
    <section v-if="content.blogExcerpts && content.blogExcerpts.length" class="bg-gray-50 py-10">
      <h2 class="text-2xl font-bold text-center mb-6">Latest Blog Posts</h2>
      <div class="flex flex-col md:flex-row gap-6 justify-center">
        <div
          v-for="(post, idx) in content.blogExcerpts"
          :key="idx"
          class="bg-white shadow rounded-lg p-4 flex-1"
        >
          <img :src="post.image" :alt="post.title" class="mb-4 rounded" />
          <h3 class="font-semibold text-lg mb-1">{{ post.title }}</h3>
          <p class="text-sm text-gray-500 mb-2">{{ post.date }} by {{ post.author }}</p>
          <p class="mb-3">{{ post.excerpt }}</p>
          <a :href="post.readMoreUrl" class="text-blue-600 hover:underline">Read more</a>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import SectionCard from '~/components/SectionCard.vue'

const content = ref({})

onMounted(async () => {
  const res = await fetch('/index.json')
  content.value = await res.json()
})
</script>
