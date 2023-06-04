<template>
  <NCard class="noprint">
    <NSpace vertical size="large">
      <NSpace justify="center">
        <NH1><NText type="primary">拼音测试生成器</NText></NH1>
      </NSpace>
      <NInput v-model:value="title" placeholder="请输入标题" />
      <NInput v-model:value="words" placeholder="请输入词语，用空格隔开" type="textarea" :autosize="{ minRows: 3 }" />
      <NSpace justify="center">
        <NButton type="primary" size="large" :disabled="!wordList?.length" @click="handlePrint">
          <template #icon>
            <PrintIcon />
          </template>
          打印
        </NButton>
      </NSpace>
    </NSpace>
  </NCard>
  <NSpace justify="center">
    <h1>{{ title }}</h1>
  </NSpace>

  <NSpace :size="0" justify="center">
    <PinyinBox v-for="word in wordList" :value="word" />
  </NSpace>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';
import { NText, NInput, NSpace, NCard, NButton, NH1 } from 'naive-ui';
import { Print as PrintIcon } from '@vicons/ionicons5';
import PinyinBox from './PinyinBox.vue';

const title = ref<string>();
const words = ref<string>();

const wordList = computed(() => words.value?.match(/\S+/g));
const handlePrint = () => window.print();
</script>
