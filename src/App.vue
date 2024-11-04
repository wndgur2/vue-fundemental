<script setup>
  import AppHeader from './components/AppHeader.vue'
  import AppBasic from './components/AppBasic.vue'
  import AppReactive from './components/AppReactive.vue'
  import { ref } from 'vue'

  const header = ref('Shopping List App')
</script>

<template>
  <AppHeader :header="header" />
  <!-- <AppBasic /> -->
  <AppReactive />
</template>
