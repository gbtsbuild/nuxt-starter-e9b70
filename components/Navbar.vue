<template>
  <nav class="bg-white border-b border-gray-100 shadow-sm">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16">
        <!-- Logo/Brand -->
        <NuxtLink to="/" class="flex items-center gap-2 font-bold text-green-700 text-xl">
          <span>MyBrand</span>
        </NuxtLink>
        <!-- Desktop Links -->
        <div class="hidden md:flex gap-8">
          <NuxtLink
            v-for="link in links"
            :key="link.label"
            :to="link.url"
            class="text-zinc-700 font-medium hover:text-green-700 transition"
            active-class="text-green-700 font-semibold"
          >
            {{ link.label }}
          </NuxtLink>
        </div>
        <!-- Mobile Hamburger -->
        <button
          class="md:hidden p-2 rounded focus:outline-none focus:ring-2 focus:ring-green-500"
          @click="open = !open"
          aria-label="Open menu"
        >
          <svg v-if="!open" class="h-6 w-6 text-zinc-700" fill="none" stroke="currentColor" stroke-width="2"
            viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
            <path d="M4 6h16M4 12h16M4 18h16"/>
          </svg>
          <svg v-else class="h-6 w-6 text-zinc-700" fill="none" stroke="currentColor" stroke-width="2"
            viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
            <path d="M6 18L18 6M6 6l12 12"/>
          </svg>
        </button>
      </div>
    </div>
    <!-- Mobile Menu -->
    <div v-if="open" class="md:hidden border-t border-gray-100 bg-white px-4 pt-2 pb-4">
      <NuxtLink
        v-for="link in links"
        :key="link.label + '-mobile'"
        :to="link.url"
        class="block py-2 text-zinc-700 font-medium hover:text-green-700"
        active-class="text-green-700 font-semibold"
        @click="open = false"
      >
        {{ link.label }}
      </NuxtLink>
    </div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'
const props = defineProps({
  links: {
    type: Array,
    default: () => [
      { label: 'Home', url: '/' },
      { label: 'Blog', url: '/blog' },
      { label: 'About', url: '/about' },
      { label: 'Contact', url: '/contact' },
    ]
  }
})
const open = ref(false)
</script>

<style scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #23272b;
  color: #fff;
  padding: 1rem 2rem;
}
.navbar-brand a {
  color: #fff;
  font-weight: bold;
  font-size: 1.4rem;
  text-decoration: none;
}
.navbar-links {
  display: flex;
  gap: 1.5rem;
  list-style: none;
  margin: 0;
  padding: 0;
}
.navbar-links a {
  color: #fff;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.2s;
}
.navbar-links a:hover {
  color: #2ecc40;
}
</style>
