<template>
  <div>
    <h2>{{ title }}</h2>
    <button @click="count++">カウント: {{ count }}</button>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      count: 0,
      title: 'カウンター',
    }
  },
}
</script>
