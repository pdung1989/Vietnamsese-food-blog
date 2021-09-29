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

    // data() {
    //   return {
    //     posts: [
    //       {
    //         title: "Pho Noodle Soup",
    //         previewText: 'The Vietnamese traditional soup you must try!',
    //         thumbnailUrl:
    //           "https://images.unsplash.com/photo-1582878826629-29b7ad1cdc43?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1074&q=80"
    //           ,
    //         id: "pho"
    //       },
    //       {
    //         title: "Vietnamese Banh mi",
    //         previewText: 'The great special sandwich of the world!',
    //         thumbnailUrl:
    //           "https://images.unsplash.com/photo-1600454309261-3dc9b7597637?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=626&q=80",
    //         id: "banhmi"
    //       }
    //     ]
    //   }
    // }
  };
</script>

<style scoped>
  #posts {
    padding-top: 1rem;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  @media (min-width: 35rem) {
    #posts {
      flex-direction: row;
    }
  }
</style>