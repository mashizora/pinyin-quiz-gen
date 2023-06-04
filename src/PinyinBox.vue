<template>
  <svg :width="20 + 60 * length" height="88">
    <line x1="10" x2="10" y1="22" y2="82" stroke="black" />
    <line x1="10" :x2="10 + length * 60" y1="22" y2="22" stroke="black" stroke-linecap="round" />
    <line x1="10" :x2="10 + length * 60" y1="82" y2="82" stroke="black" stroke-linecap="round" />
    <line x1="10" :x2="10 + length * 60" y1="52" y2="52" stroke="black" stroke-width="0.5" stroke-dasharray="5" stroke-dashoffset="2.5" />
    <template v-for="(p, index) in result">
      <text :x="40 + 60 * index" y="16" font-size="16" text-anchor="middle">{{ p }}</text>
      <line :x1="70 + 60 * index" :x2="70 + 60 * index" y1="22" y2="82" stroke="black" />
      <line :x1="40 + 60 * index" :x2="40 + 60 * index" y1="22" y2="82" stroke="black" stroke-width="0.5" stroke-dasharray="5" stroke-dashoffset="2.5" />
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
