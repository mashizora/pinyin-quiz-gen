<template>
  <svg :width="20 + 60 * length" height="100">
    <line x1="10" x2="10" y1="30" y2="90" stroke="black" />
    <line x1="10" :x2="10 + length * 60" y1="30" y2="30" stroke="black" stroke-linecap="round" />
    <line x1="10" :x2="10 + length * 60" y1="90" y2="90" stroke="black" stroke-linecap="round" />
    <line x1="10" :x2="10 + length * 60" y1="60" y2="60" stroke="black" stroke-width="0.5" stroke-dasharray="5" stroke-dashoffset="2.5" />
    <template v-for="(p, index) in result">
      <text :x="40 + 60 * index" y="22" font-size="20" text-anchor="middle">{{ p }}</text>
      <line :x1="70 + 60 * index" :x2="70 + 60 * index" y1="30" y2="90" stroke="black" />
      <line :x1="40 + 60 * index" :x2="40 + 60 * index" y1="30" y2="90" stroke="black" stroke-width="0.5" stroke-dasharray="5" stroke-dashoffset="2.5" />
    </template>
  </svg>
</template>

<script setup lang="ts">
import { computed } from 'vue';
import { pinyin } from 'pinyin-pro';

const { value } = defineProps<{ value: string }>();

const result = computed(() => pinyin(value, { type: 'array' }));
const length = computed(() => result.value.length);
</script>
