<template>
  <div class="flex items-center justify-center gap-3 flex-wrap">
    <base-card
      v-for="card in cardsData"
      :key="card.id"
      :card="card"
    />
  </div>
</template>

<script setup>
import BaseCard from '@/components/BaseCard';

import { computed, ref } from 'vue';

import axios from 'axios';

const props = defineProps({
  inputText: {
    type: String,
    default: ''
  }
});

const data = ref([]);

const cardsData = computed(() => props.inputText ? data.value.filter(item => item.username.toLowerCase().includes(props.inputText.toLowerCase())) : data.value);

const getData = async () => {
  const postsResponse = await axios.get('http://jsonplaceholder.typicode.com/posts');
  const usersResponse = await axios.get('http://jsonplaceholder.typicode.com/users');
  data.value = postsResponse.data.map(item => {
    for (const user of usersResponse.data) {
      if (user.id === item.userId) {
        return {
          ...item,
          username: user.name
        }
      }
    }
  });
};

await getData();
</script>
