<template>
  <footer class="bg-white border-t-2 border-green-500 mt-16 pt-10 pb-6 px-4 sm:px-10">
    <div class="max-w-7xl mx-auto flex flex-col md:flex-row md:justify-between gap-8">
      <!-- Links Section -->
      <div>
        <div class="flex flex-wrap gap-4 mb-4">
          <a v-for="link in links" :key="link.url" :href="link.url" class="text-green-600 hover:text-green-800 font-semibold transition-colors">
            {{ link.label }}
          </a>
        </div>
        <p class="text-sm text-gray-500">{{ copyright }}</p>
      </div>
      <!-- Address & Contact Section -->
      <div>
        <address class="not-italic text-gray-700 text-sm mb-2">
          <div>{{ address.line1 }}</div>
          <div>{{ address.line2 }}</div>
        </address>
        <div class="text-gray-700 text-sm mb-2">
          Email:
          <a :href="`mailto:${contact.email}`" class="text-green-700 hover:underline ml-1">{{ contact.email }}</a>
        </div>
        <div class="text-gray-700 text-sm">
          Phone:
          <a :href="`tel:${contact.phone}`" class="text-green-700 hover:underline ml-1">{{ contact.phone }}</a>
        </div>
      </div>
      <!-- Social Media -->
      <div class="flex items-center gap-4">
        <a
          v-for="s in social"
          :key="s.platform"
          :href="s.url"
          target="_blank"
          rel="noreferrer"
          class="text-green-600 hover:text-green-800 text-2xl transition-colors"
        >
          <i :class="getIconClass(s.platform)"></i>
        </a>
      </div>
    </div>
  </footer>
</template>

<script setup>
const props = defineProps({
  links: Array,
  address: Object,
  contact: Object,
  social: Array,
  copyright: String
})

function getIconClass(platform) {
  switch ((platform || '').toLowerCase()) {
    case 'facebook':
      return 'fab fa-facebook-f'
    case 'twitter':
      return 'fab fa-twitter'
    case 'instagram':
      return 'fab fa-instagram'
    case 'pinterest':
      return 'fab fa-pinterest'
    case 'whatsapp':
      return 'fab fa-whatsapp'
    default:
      return 'fas fa-globe'
  }
}
</script>
