<template>
  <div class="bg-white p-3 rounded-lg w-1/4 flex flex-col gap-3">
    <div class="font-semibold text-lg text-blue-700">{{ card.title }}</div>
    <div>{{ card.body }}</div>
    <div class="font-light text-gray-500">{{ card.username }}</div>
  </div>
</template>

<script setup>
defineProps({
  card: {
    type: Object,
    default: () => ({})
  }
});
</script>
