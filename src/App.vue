<template>
  <div>
    <LayoutWrap>
      on slot
      {{countOnSlot}}
    </LayoutWrap>
    <button @click="addSlotCount">addSlotCount</button>
  </div>
  <div>
    <div>
      on slot
      {{countOnDiv}}
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
onBeforeUpdate(()=>{
  console.log('onBeforeUpdate');
})

</script>
