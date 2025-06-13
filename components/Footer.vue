<template>
  <footer class="footer">
    <div class="footer-links">
      <a
        v-for="link in links"
        :key="link.url"
        :href="link.url"
        class="footer-link"
      >
        {{ link.label }}
      </a>
    </div>
    <address>
      {{ address.line1 }}<br />
      {{ address.line2 }}<br />
      Email:
      <a :href="`mailto:${contact.email}`">
        {{ contact.email }}
      </a>
      <br />
      Phone:
      <a :href="`tel:${contact.phone}`">
        {{ contact.phone }}
      </a>
    </address>
    <div class="social-media">
      <a
        v-for="s in social"
        :key="s.platform"
        :href="s.url"
        target="_blank"
        rel="noreferrer"
        class="social-link"
      >
        <i :class="getIconClass(s.platform)"></i>
      </a>
    </div>
    <p class="copyright">{{ copyright }}</p>
  </footer>
</template>

<script setup>
defineProps({
  links: Array,
  address: Object,
  contact: Object,
  social: Array,
  copyright: String
})

function getIconClass(platform) {
  switch (platform.toLowerCase()) {
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
      return ''
  }
}
</script>

<style scoped>
.footer {
  background: #23272b;
  color: #fff;
  text-align: center;
  padding: 2rem 1rem;
}
.footer-links {
  margin-bottom: 1rem;
}
.footer-link {
  margin: 0 0.6rem;
  color: #fff;
  text-decoration: none;
  font-weight: 500;
}
.footer-link:hover {
  text-decoration: underline;
}
address {
  font-style: normal;
  margin-bottom: 1rem;
}
.social-media {
  margin: 1rem 0;
}
.social-link {
  margin: 0 0.5rem;
  color: #fff;
  font-size: 1.3rem;
  transition: color 0.2s;
}
.social-link:hover {
  color: #2ecc40;
}
.copyright {
  font-size: 0.95rem;
  color: #bbb;
  margin-top: 1.5rem;
}
</style>
