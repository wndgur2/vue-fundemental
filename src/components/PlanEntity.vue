<script setup lang="ts">
  import { ref } from 'vue'
  let props = defineProps(['name'])
  let name = props.name
  let selected = ref(false)
  const emit = defineEmits(['sel', 'select'])

  const select = () => {
    selected.value = true
    emit('sel', 'selection happened on', name)
  }
</script>

<template>
  <div @click="select">
    <h3 :class="[{ 'active-plan': selected }]">{{ name }}</h3>
  </div>
</template>

<style>
  .active-plan {
    color: red;
  }
</style>
