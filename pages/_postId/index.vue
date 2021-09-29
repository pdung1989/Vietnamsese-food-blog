<template>
  <div id="post">
    <div id="thumbnail-image" :style="{backgroundImage: 'url(' + image + ')'}"></div>
    <section class="post-content">
      <h1>{{ title }}</h1>
      <p>{{ content }}</p>
    </section>
  </div>
</template>

<script>

export default {
 asyncData(context) {
    return context.app.$storyapi
      .get("cdn/stories/blog/" + context.params.postId, {
        version: "draft"
      })
      .then(res => {
        return {
          image: res.data.story.content.thumbnail,
          title: res.data.story.content.title,
          content: res.data.story.content.content
        };
      });
  }
};
</script>

<style scoped>

  #thumbnail-image {
    background-position: center; 
    background-repeat: no-repeat;
    width: 50%; 
    border-radius: 35px;
  }

  .post-content {
    width: 50%;
    max-width: 500px;
    margin: auto;
    padding-left: 1rem
  }

  .post-content p {
    white-space: pre-line;
  
  }

  #post {
    display: flex;
    margin: 1rem;
    padding: 3rem;
    height: 35rem;
    width: 100%;
    border-radius: 4px;
    box-shadow: 1px 1px 3px 1px rgb(41, 35, 35);
  }

</style>