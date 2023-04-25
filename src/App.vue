<template>
  <div>
    <LayoutWrap>
      on slot
      <template v-for="(value,index) in list" :key="value">
        <div v-show="index===countOnSlot" :ref="setRefInSlot">{{ value }}</div>
      </template>
    </LayoutWrap>
    <button @click="addSlotCount">addSlotCount</button>
  </div>
  <div>
    <div>
      on slot
      <template v-for="(value,index) in list" :key="value">
        <div v-show="index===countOnDiv" :ref="setRefInDiv">{{ value }}</div>
      </template>
    </div>
    <button @click="addDivCount">addDivCount</button>
  </div>
</template>

<script setup>
import {ref,onBeforeUpdate} from 'vue';
import LayoutWrap from '@/components/LayoutWrap.vue';
const countOnSlot=ref(0)
const countOnDiv=ref(0)

const addSlotCount=()=>{
  countOnSlot.value++
}
const addDivCount=()=>{
  countOnDiv.value++
}
const list=ref([1,2,3,4,5])
const setRefInSlot=(el)=>{
  console.log('setRefInSlot el:',el);
}
const setRefInDiv=(el)=>{
  console.log('setRefInDiv el:',el);
}
onBeforeUpdate(()=>{
  console.log('onBeforeUpdate');
})

</script>
