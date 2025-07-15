<script setup lang="ts">
defineProps<{ msg: string }>()
</script>

<template>
  <div class="hello">
    <h2>Hello World</h2>
    <p>{{ msg }}</p>
  </div>
</template>

<style scoped>
.hello {
  color: #42b983;
  font-weight: bold;
}
</style>
