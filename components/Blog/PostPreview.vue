<template>
  <nuxt-link 
    :to="id">
    <article class="post-preview">
      <div
        :style="{backgroundImage: 'url(' + thumbnailImage + ')'}" 
        class="post-preview-thumbnail"></div>
      <div class="post-preview-content">
        <h1>{{ title }}</h1>
        <p>{{ previewText }}</p>
      </div>
    </article>
  </nuxt-link>
</template>

<script>

export default {
  props: {
    title: {
      type: String,
      required: true
    },
    previewText: {
      type: String,
      required: true
    },
    thumbnailImage: {
      type: String,
      required: true
    },
    id: {
      type: String,
      required: true
    }
  }
}
</script>

<style>
a {
  text-decoration: none;
  color: black;
}

.post-preview {
  margin: 1rem;
  height: 20rem;
  width: 90%;
  border-radius: 4px;
  box-shadow: 1px 1px 3px 1px rgb(41, 35, 35);
}

.post-preview-thumbnail {
  background-position: center;
  background-size: cover;
  width: 100%;
  height: 13rem;
}

.post-preview-content {
  text-align: center;
  margin: auto;
  padding: 0.5rem;
}

@media (min-width: 35rem) {
  .post-preview {
    width: 25rem;
  }
}
</style>