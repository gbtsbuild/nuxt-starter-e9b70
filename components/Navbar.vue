<template>
  <nav class="navbar">
    <div class="navbar-brand">
      <a href="/">GBTS Builders Solution Ltd</a>
    </div>
    <ul class="navbar-links">
      <li v-for="link in links" :key="link.url">
        <a :href="link.url">{{ link.label }}</a>
      </li>
    </ul>
  </nav>
</template>

<script setup>
// Example: Accept links as props or hardcode for now
const links = [
  { label: "Home", url: "/" },
  { label: "Roofings", url: "/roofings" },
  { label: "Hand Tools", url: "/hand-tools" },
  { label: "Locks & Knobs", url: "/locks-knobs" },
  { label: "Security Cameras", url: "/security-cameras" },
  { label: "Appliances", url: "/appliances" },
  { label: "Blog", url: "/blog-posts" }
]
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
