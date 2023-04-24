<template>
  <LayoutWrap>
    on slot
    <template v-for="value in list" :key="value">
      <div v-show="index===value"  :ref="refs.set">{{ value }}</div>
    </template>
    <div>refs.length:{{ refs.length }}</div>
  </LayoutWrap>
  <br>
  <div>
    on div
    <template v-for="value in list" :key="value">
      <div v-show="index===value"  :ref="refs2.set">{{ value }}</div>
    </template>
    <div>refs2.length:{{ refs2.length }}</div>
  </div>
  <div>
    <button @click="addCount">+1</button>
    {{ index }}
    <button @click="subCount">-1</button>
  </div>
</template>

<script setup>
import {  ref } from 'vue';
import { useTemplateRefsList } from '@vueuse/core';
import LayoutWrap from '@/components/LayoutWrap.vue';

let index = ref(1);
const list=ref([1,2,3])
const refs = useTemplateRefsList();
const refs2 = useTemplateRefsList();
const addCount=()=>{
  index.value++
}
// 减一
const subCount=()=>{
  index.value--
}
</script>
