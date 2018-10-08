<template>
    <nuxt-link :to="id">
      <article class="post-preview">
        <div class="post-preview-thumbnail" :style="{backgroundImage: 'url(' + thumbnailImage + ')'}"></div>
        <div class="post-preview-content">
          <h1>{{ title }}</h1>
          <p>{{ excerpt }}</p>
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
      excerpt: {
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

<style scoped>
  .container {
    margin: 0 auto !important;
  }
  a {
    text-decoration: none;
    color: #252525;
  }
  .post-preview {
    border-radius: 3px;
    box-shadow: 1px 1px 5px 1px rgba(0,0,0,0.5);
    width: 90%;
    margin: auto;
    height: 30rem;
    margin: 1rem;
  }
  .post-preview-thumbnail {
    background-position: center;
    background-size: cover;
    width: 100%;
    height: 20rem;
  }
  .post-preview-content {
    text-align: center;
    padding: 2rem;
  }

  @media (min-width: 35rem) {
    .post-preview {
      width: 25rem;
    }
  }
</style>

