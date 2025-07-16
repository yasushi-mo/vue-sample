<script setup lang="ts">
import { ref, onMounted } from 'vue'
import axios from 'axios'

type Post = {
  id: number
  title: string
  body: string
}

const posts = ref<Post[]>([])
const isLoading = ref(true)
const err = ref('')

// コンポーネントマウント時にデータ取得
onMounted(async () => {
  try {
    const response = await axios.get<Post[]>('https://jsonplaceholder.typicode.com/posts')
    posts.value = response.data
  } catch (error) {
    err.value = 'Failed to getting data:' + JSON.stringify(error)
  } finally {
    isLoading.value = false
  }
})
</script>

<template>
  <div>
    <h2>投稿一覧</h2>

    <p v-if="isLoading">読み込み中...</p>
    <p v-if="err">{{ err }}</p>

    <ul v-else>
      <li v-for="post in posts" :key="post.id">
        <h3>{{ post.title }}</h3>
        <p>{{ post.body }}</p>
      </li>
    </ul>
  </div>
</template>

<style scoped>
h2 {
  color: #2c3e50;
  margin-bottom: 1rem;
}

li {
  margin-bottom: 1rem;
}
</style>
