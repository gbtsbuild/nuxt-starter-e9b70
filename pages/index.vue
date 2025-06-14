<template>
  <section class="hero">
    <nav class="navbar">
      <div class="brand">
        <span class="brand-icon" aria-label="logo">🏗️</span>
        <span class="brand-name">GBTS Builders Solution Ltd</span>
      </div>
      <div class="nav-links">
        <button class="nav-btn">Sign Up</button>
        <button class="nav-btn outline">Log In</button>
      </div>
    </nav>
    <div class="hero-content">
      <div class="hero-text">
        <h1>
          Your One-Stop-Shop For Building Materials<br />
          with <span class="highlight2">GBTS Builders Solution Ltd</span>
        </h1>
        <p>
          Craft high-performing, reliable, and beautiful buildings and homes with our top-quality materials, expert advice, and trusted service.<br />
          Experience the GBTS difference with speed, quality, and care.
        </p>
        <button class="cta-btn">Get Started Today</button>
      </div>
      <div class="hero-image">
        <!-- Replace the src below with your own image or illustration -->
        <img src="https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=600&q=80" alt="Modern building illustration" />
      </div>
    </div>
</template>
.hero-content {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
  padding: 48px 8vw 0 8vw;
  gap: 40px;
}
.hero-text {
  max-width: 500px;
}
.hero-text h1 {
  font-size: 2.8rem;
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 18px;
  color: #222;
}
.highlight2 {
  color: #fff;
  background: #1168e6;
  border-radius: 4px;
  padding: 2px 8px;
  font-weight: 600;
}
.hero-text p {
  font-size: 1.20rem;
  color: #4a5568;
  margin-bottom: 24px;
}
.cta-btn {
  padding: 12px 32px;
  font-size: 1.1rem;
  background: linear-gradient(120deg, #1168e6 60%, #49b5c2 100%);
  color: #fff;
  border: none;
  border-radius: 6px;
  font-weight: 600;
  box-shadow: 0 4px 16px rgba(17,104,230,0.10);
  transition: background 0.2s, box-shadow 0.2s;
  cursor: pointer;
}
.cta-btn:hover {
  background: linear-gradient(120deg, #49b5c2 0%, #1168e6 100%);
  box-shadow: 0 8px 24px rgba(17,104,230,0.18);
}
.hero-image img {
  width: 350px;
  height: 280px;
  object-fit: cover;
  border-radius: 20px;
  box-shadow: 0 8px 32px rgba(50,100,200,0.08);
  background: #fff;
  border: 1.5px solid #eaeaea;
}
.trusted-by {
  margin: 64px 0 0 0;
  text-align: center;
  color: #6b7280;
  font-size: 1rem;
}
.brand-logos {
  margin-top: 18px;
  display: flex;
  justify-content: center;
  gap: 36px;
  align-items: center;
}
.brand-logos img {
  width: 38px;
  height: 38px;
  filter: grayscale(1) brightness(0.8);
  transition: filter 0.2s;
}
.brand-logos img:hover {
  filter: grayscale(0) brightness(1);
}
</style>

<style scoped>
.hero {
  min-height: 100vh;
  background: linear-gradient(120deg, #f8fafc 0%, #e0e7ef 100%);
  display: flex;
  flex-direction: column;
  padding-bottom: 40px;
}
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 32px 8vw 0 8vw;
}
.brand {
  display: flex;
  align-items: center;
  font-weight: bold;
  font-size: 1.5rem;
  color: #333;
}
.brand-icon {
  font-size: 2rem;
  margin-right: 10px;
}
.brand-name {
  letter-spacing: 1px;
}
.nav-links {
  display: flex;
  gap: 12px;
}
.nav-btn {
  padding: 8px 20px;
  background: #1168e6;
  color: #fff;
  border: none;
  border-radius: 6px;
  font-weight: 500;
  cursor: pointer;
  transition: background 0.2s;
}
.nav-btn.outline {
  background: transparent;
  color: #1168e6;
  border: 1.5px solid #1168e6;
}
.nav-btn:hover {
  background: #084d9a;
  color: #fff;
}

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
