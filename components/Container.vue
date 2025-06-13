<template>
  <div class="container">
    <slot />
  </div>
</template>

<style scoped>
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2.5rem 1.2rem;
  background: #fff;
  border-radius: 20px;
  box-shadow: 0 4px 32px rgba(46, 204, 64, 0.07);
  min-height: 90vh;
}
@media (max-width: 600px) {
  .container {
    padding: 1rem 0.5rem;
    border-radius: 10px;
  }
}
</style>
