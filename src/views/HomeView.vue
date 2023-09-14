<template>
  <div class="home">
    <h1>Home</h1>
    <input type="text" v-model="search">
    <p>search term - {{ search }}</p>
    <button @click="handleClick">stop watching</button>
    <div v-for="name in matchingNames" :key="name">{{ name }}</div>
  </div>
</template>

<script>
import { computed, ref, watch, watchEffect } from 'vue'

export default {
  name: 'HomeView',
  setup() {
    const search = ref('')
    const names = ref(['mario', 'yoshi', 'luigi', 'toad', 'bowser', 'koopa', 'peach'])

    // the callback fires every time the search changes
    // does't run initially
    const stopWatch = watch(search, () => {
      console.log('watch function ran')
    })

    // 1) run initially when the component first loads (when setup() func first runs)
    const stopEffect = watchEffect(() => {
      // 2) runs only when any value that we use inside it changes
      // in this case -- search.value
      console.log('watchEffect function ran', search.value)
    })

    // 3) to stop them watching we need to invoke those functions
    const handleClick = () => {
      stopWatch()
      stopEffect()
    }

    const matchingNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value))
    })

    return { names, search, matchingNames, handleClick }
  }
}
</script>
