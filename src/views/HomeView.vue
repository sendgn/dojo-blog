<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error" class="error">{{ error }}</div>
    <div v-if="posts.length" class="layout">
      <PostList :posts="posts" />
      <TagCloud :posts="posts" />
    </div>
    <div v-else-if="!error">
      <PendingSpinner />
    </div>
  </div>
</template>

<script>
  import getPosts from '../composables/getPosts'
  import PostList from '../components/PostList.vue'
  import PendingSpinner from '../components/PendingSpinner.vue'
  import TagCloud from '../components/TagCloud.vue'

  export default {
    name: 'HomeView',
    components: { PostList, PendingSpinner, TagCloud },
    setup() {
      const { posts, error, load } = getPosts()

      load()

      return { posts, error }
    }
  }
</script>

<style>
  .home {
    max-width: 1200px;
    margin: 0 auto;
    padding: 10px;
  }
</style>