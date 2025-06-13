<template>
  <Navbar />
  <slot />
  <Footer
    :links="page.footer.links"
    :address="page.footer.address"
    :contact="page.footer.contact"
    :social="page.footer.social"
    :copyright="page.footer.copyright"
  />
</template>

<script setup>
import { ref } from 'vue'
import pageData from '@/data/index.json'

// Provide page data to Footer (and other components if needed)
const page = ref(pageData)
</script>
