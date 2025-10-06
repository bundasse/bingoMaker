<script setup>
import { ref, computed } from 'vue';
// const props = defineProps(() => {

// })
  const bingoSize =ref(3)
  const bingoWidth = computed(() => {
    return (600 - 4*(bingoSize.value-1))/bingoSize.value
  })
  const bingoArray = ref(['val1','val2','val3','val4','val5','val6','val7','val8','val9'])
  </script>
<template>
    <div>
    <div class="bingoArea" :style="`grid: repeat(${bingoSize}, 1fr) / repeat(${bingoSize}, 1fr);`">
      <div class="bingoCell" :style="`width: ${bingoWidth}px; height: ${bingoWidth}px;`" v-for="row in Math.pow(bingoSize,2)" :key="row">
        <p class="bingoText">{{ bingoArray[row-1] }}</p>
      </div>
    </div>
    </div>
</template>
<style>
.bingoArea{
  width: 600px;
  height: 600px;
  display: grid;
  gap: 4px;
}
.bingoCell{
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: none;
  border: 1px solid steelblue;
  border-radius: 12px;
  padding: 12px 0;
}
.bingoText{
  font-size: 1.2rem;
}
</style>
