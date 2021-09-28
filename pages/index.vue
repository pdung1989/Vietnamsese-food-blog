<template>
  <section class="container">
    <nuxt-link 
      v-for="post in posts"
      :key="post.id"
      to="post.id"
    >
      <article class="post-preview">
        <div
          :style="{backgroundImage: post.thumbnailUrl}" 
          class="post-preview-thumbnail">
        </div>
        <div class="post-preview-content">
          <h1>{{ post.title }}</h1>
          <p>{{ post.prevewText }}</p>
        </div>
      </article>
    </nuxt-link>
  </section>
</template>

<script>
  export default {
    data() {
      return {
        posts: [
          {
            title: "Pho Noodle Soup",
            prevewText: 'The Vietnamese traditional noodle soup you must try!',
            thumbnailUrl:
              "https://www.hungryhuy.com/chicken-pho-recipe/",
            id: "pho"
          },
          {
            title: "Vienamese sandwich - Banh mi",
            prevewText: 'The great special sandwich of the world!',
            thumbnailUrl:
              "https://www.hungryhuy.com/banh-mi-recipe/",
            id: "banhmi"
          }
        ]
      }
    }
  };
</script>

<style>
</style>