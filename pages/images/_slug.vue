<template>
    <div>
      <h1>{{ image.title }}!!</h1>
      <pre>{{ image }}</pre>
      <p>{{ image.prompt }}</p>
      <!-- Use nuxt-img to display the image from static folder -->
      <nuxt-img :src="image.image" :alt="image.alt" class="my-8" format="webp" />
      
      <p><strong>Date:</strong> {{ image.date }}</p>
      <div>
        <strong>Tags:</strong>
        <ul>
          <li v-for="tag in image.tags" :key="tag">{{ tag }}</li>
        </ul>
      </div>
      <nuxt-content :document="image" />
    </div>
  </template>
  
  <script>
  export default {
    async asyncData({ $content, params }) {
      const image = await $content('images', params.slug).fetch()
      return { image }
    }
  }
  </script>