<template>
  <div class="flex items-center flex-col py-16 gap-14">
    <base-input
      v-model="inputText"
    />
    <suspense>
      <base-card-list
        :inputText="inputText"
      />
      <template #fallback>
        <div class="text-3xl font-semibold">
          Идет загрузка данных...
        </div>
      </template>
    </suspense>
  </div>
</template>

<script setup>
import BaseInput from '@/components/BaseInput';
import BaseCardList from '@/components/BaseCardList';

import { ref } from 'vue';

const inputText = ref('');
</script>
