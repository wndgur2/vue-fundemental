<script setup>
  import { ref, reactive } from 'vue'
  const state = reactive({ count: 0 })
  const increment = () => {
    state.count++
  }
</script>

<template>
  <h1>{{ state.count }}</h1>
  <button @click="increment">Increment count</button>
</template>
