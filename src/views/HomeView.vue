<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error" class="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList :posts="posts" />
    </div>
    <div v-else-if="!error">
      <PendingSpinner />
    </div>
  </div>
</template>

<script>
import PostList from '../components/PostList.vue'
import getPosts from '../composables/getPosts'
import PendingSpinner from '../components/PendingSpinner.vue'

export default {
  name: 'HomeView',
  components: { PostList, PendingSpinner },
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