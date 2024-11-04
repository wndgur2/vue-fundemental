<script setup>
  import { ref, computed } from 'vue'

  const editing = ref(false)
  const newItem = ref('')
  const newItemHighPriority = ref(false)
  const items = ref([
    { id: 2, label: '2 board games', purchased: false, prior: false },
    { id: 3, label: '20 cups', purchased: true, prior: true },
    { id: 4, label: '40 cups', purchased: true, prior: false },
  ])

  // do not alter data here
  const reversedItems = computed(() => [...items.value].reverse())

  const add = () => {
    items.value.push({
      id: items.value.length + 1,
      label: newItem.value,
      purchased: false,
      prior: newItemHighPriority.value,
    })
    newItem.value = ''
  }
  const doEdit = (_editing) => {
    editing.value = _editing
    newItem.value = ''
  }

  const togglePurchased = (item) => {
    item.purchased = !item.purchased
  }
</script>
<template>
  <button
    v-if="editing"
    @click="doEdit(false)"
  >
    Cancel
  </button>
  <button
    v-else
    @click="doEdit(true)"
  >
    Add Item
  </button>
  <form
    @submit.prevent="add"
    v-if="editing"
  >
    <input
      type="text"
      placeholder="Add an item"
      v-model.trim="newItem"
    />
    Priority:
    <label>
      <input
        type="checkbox"
        v-model="newItemHighPriority"
      />
      HighPriority
    </label>
    <br />
    <button :disabled="newItem.length < 3">Save Item</button>
  </form>
  <ul>
    <li
      v-for="item in reversedItems"
      class="static-class"
      :class="{ strikeout: item.purchased, priority: item.prior }"
      @click="togglePurchased(item)"
    >
      {{ item.label }}
    </li>
    <!-- <li
      v-for="{ id, label, purchased, prior } in items"
      :key="id"
      class="static-class"
      :class="[{ 'strikeout text-gray': purchased }, { priority: prior }]"
    >
      {{ label }}
    </li> -->
  </ul>
  <p v-if="!items.length">Nothing to see here</p>
</template>
