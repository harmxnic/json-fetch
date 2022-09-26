<template>
  <input class="p-2 rounded w-1/4 border border-solid border-gray-300"
    :value="modelValue"
    @input="updateValue"
    type="text"
    placeholder="Введите автора"
  >
</template>

<script setup>
const emits = defineEmits(['update:modelValue']);
defineProps({
  modelValue: String
});

const updateValue = (event) => {
  emits('update:modelValue', event.target.value);
};
</script>
