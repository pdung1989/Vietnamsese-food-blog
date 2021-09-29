<template>
  <section id="posts">
    <PostPreview 
      v-for="post in posts"
      :key="post.id"
      :title="post.title"
      :previewText="post.previewText"
      :thumbnailImage="post.thumbnailUrl"
      :id="post.id"/>
  </section>
</template>

<script>
  import PostPreview from '@/components/Blog/PostPreview';

  export default {
    components: {
      PostPreview
    },

    asyncData(context) {
    return context.app.$storyapi
      .get('cdn/stories', {
        version: "draft",
        starts_with: 'blog/'
      })
      .then(res => {
        return {
          posts: res.data.stories.map(bp => {
            return {
              id: bp.slug,
              title: bp.content.title,
              previewText: bp.content.summary,
              thumbnailUrl: bp.content.thumbnail
            };
          })
        };
      });
    }
  };
</script>

<style scoped>
  #posts {
    padding-top: 1rem;
    display: flex;
  }

  @media (min-width: 35rem) {
    #posts {
      flex-direction: row;
    }
  }
</style>