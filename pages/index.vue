 <script setup>
import { ref } from 'vue'
import pageData from '@/data/index.json'
const page = ref(pageData)

definePageMeta({
  layout: "default",
});
</script>

<template>
  <Container>
    <Hero
      :title="page.hero.title"
      :description="page.hero.description"
      :image="page.hero.image"
      :imageAlt="page.hero.imageAlt"
      :buttons="page.hero.buttons"
    />
    <Features
      :title="page.features.title"
      :description="page.features.description"
      :items="page.features.items"
    />

    <!-- Main Sections -->
    <div>
      <SectionCard
        v-for="section in page.sections"
        :key="section.title"
        :title="section.title"
        :subtitle="section.subtitle"
        :description="section.description"
        :image="section.image"
        :cta="section.cta"
      />
    </div>

    <!-- Blog Excerpts -->
    <div>
      <BlogExcerpt
        v-for="blog in page.blogExcerpts"
        :key="blog.slug"
        :title="blog.title"
        :excerpt="blog.excerpt"
        :author="blog.author"
        :date="blog.date"
        :image="blog.image"
        :readMoreUrl="blog.readMoreUrl"
      />
    </div>

    <!-- Footer -->
    <FooterComponent
      :links="page.footer.links"
      :address="page.footer.address"
      :contact="page.footer.contact"
      :social="page.footer.social"
      :copyright="page.footer.copyright"
    />
  </Container>
</template>
