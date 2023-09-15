<template>
  <div class="home">
    <h1>Home</h1>
    <PostList v-if="showPosts" :posts="posts" />
    <button @click="showPosts = !showPosts">toggle posts</button>
    <button @click="posts.pop()">delete a post</button>
  </div>
</template>

<script>
import PostList from '../components/PostList.vue'
import { ref } from 'vue'

export default {
  name: 'HomeView',
  components: { PostList },
  setup() {
    const posts = ref([
      { title: 'welcome to the blog', body: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Tempora odit dolore voluptatum voluptas commodi id unde consequuntur molestias? Praesentium iste accusantium modi a dolorem, minima dolore beatae adipisci architecto rem suscipit voluptatum deleniti eum in officiis earum pariatur maiores tempora consequatur reprehenderit neque! Et doloremque, rerum nostrum ipsum placeat illo architecto vel quidem similique consequatur qui assumenda ex distinctio libero quasi. Necessitatibus excepturi, eaque cum corrupti eos est alias delectus distinctio officiis ex tenetur voluptates impedit neque quasi dignissimos aspernatur illo provident? Ut delectus assumenda rerum possimus quam sunt optio, nisi dolore, ad nesciunt unde fugiat. Reiciendis illum molestiae ea?', id: 1 },
      { title: 'top 5 CSS tips', body: 'lorem ipsum', id: 2 },
    ])
    const showPosts = ref(true)

    return { posts, showPosts }
  }
}
</script>
