<script setup>
  import PlanEntity from './PlanEntity.vue'
  const plans = ['Algo study', 'apply', 'codingTest', 'CS']
</script>

<template>
  <div>
    <PlanEntity
      v-for="plan in plans"
      :name="plan"
      @sel="(a, b) => console.log(a, b, c)"
    />
  </div>
</template>
