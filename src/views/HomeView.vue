<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList :posts="posts" />
    </div>
    <div v-else>
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
