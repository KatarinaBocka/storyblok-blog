<template>
  <section id="posts">
    <PostPreview v-for="post in posts" :key="post.id" :title="post.title" :excerpt="post.previewText" :thumbnailImage="post.thumbnailUrl" :id="post.id"/>
  </section>
</template>

<script>

import PostPreview from "@/components/Blog/PostPreview";
export default {
  components: {
    PostPreview
  },
  asyncData(context) {
    return context.app.$storyapi
    .get("cdn/stories", {
      version: "draft",
      starts_with: "blog/"
    })
    .then(res => {
      console.log(res);
      return {
        posts: res.data.stories.map(blogPost => {
          return {
            id: blogPost.slug,
            title: blogPost.content.content,
            previewText: blogPost.content.summary,
            thumbnailUrl: blogPost.content.thumbnail
          };
        })
      };
    });
  }
  // data() {
  //   return {
  //     posts: [
  //     {
  //       title: "A New Begining",
  //       previewText: "This will be awesome, don\'t miss it!",
  //       thumbnailUrl: "https://taniakowalski.com/wp-content/uploads/2018/02/Healthy-Fat-Loss-Tips.jpg",
  //       id: "a-new-begining"
  //     },
  //     {
  //       title: "A Second Begining",
  //       previewText: "This will be awesome, don\'t miss it!",
  //       thumbnailUrl: "https://storage-cube.quebecormedia.com/v1/dynamic_resize?quality=75&size=1500x1500&src=http%3A%2F%2Fstorage-cube.quebecormedia.com%2Fv1%2Fcl_prod%2Fcanadian_living%2Fbb92658b-5af7-47ad-ba3a-e1aea911e2c7%2F25-healthy-fruits-image1424807763.jpg",
  //       id: "a-second-begining"
  //     },
  //     ]
  //   }
  // }
}
</script>

<style scoped>
#posts {
  padding-top: 2rem;
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
