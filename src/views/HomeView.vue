<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList :posts="posts" />
    </div>
    <div v-else style="color: crimson; font-size: 2em;">Loading...</div>
  </div>
</template>

<script>
import PostList from '../components/PostList.vue'
import { ref } from 'vue'

export default {
  name: 'HomeView',
  components: { PostList },
  setup() {
    const posts = ref([])
    const error = ref(null)

    const load = async () => {
      try {
        let data = await fetch('http://localhost:3000/posts')
        if (!data.ok) {
          throw new Error("Could't fetch the data")
        }
        posts.value = await data.json()
      } catch (err) {
        error.value = err.message
      }
    }

    load()

    return { posts, error }
  }
}
</script>
