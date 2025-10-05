<script setup>
import { ref } from 'vue';
// const props = defineProps(() => {

// })
  const bingoSize =ref(3)
  </script>
<template>
    <div>
        <div class="bingoArea" :style="`grid: repeat(${bingoSize}, 1fr) / repeat(${bingoSize}, 1fr);`">
      <div class="bingoCell" :style="`width: ${bingoWidth}px; height: ${bingoWidth}px;`" v-for="row in Math.pow(bingoSize,2)" :key="row">
        <textarea :style="`width: ${bingoWidth-3}px;`" ref="bingoInputBox" rows="1" class="bingoInput" @keyup="changeTextHeight(row-1)"></textarea>
      </div>
    </div>
    </div>
</template>
<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
.bingoArea{
  width: 600px;
  height: 600px;
  display: grid;
  gap: 4px;
}
.bingoCell{
  align-items: stretch;
  display: flex;
  align-items: center;
  background-color: none;
  border: 1px solid steelblue;
  border-radius: 12px;
  padding: 12px 0;
}
.bingoInput{
  background: none;
  outline: none;
  border: 1px solid transparent;
  font-size: 1.2rem;
  resize: none;
  overflow: hidden;
}
.bingoInput:focus{
  border: 1px solid lightblue;
}
</style>
