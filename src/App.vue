<script setup>
  import PlanEntity from './components/PlanEntity.vue'
  import AppHeader from './components/AppHeader.vue'
  import AppBasic from './components/AppBasic.vue'
  import AppReactive from './components/AppReactive.vue'
  import { ref } from 'vue'
  import PlanPicker from './components/PlanPicker.vue'
  const header = ref('Shopping List App')
</script>

<template>
  <AppHeader :header="header" />
  <PlanPicker />
  <!-- <AppBasic /> -->
  <!-- <AppReactive /> -->
</template>
