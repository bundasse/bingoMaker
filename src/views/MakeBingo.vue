<script setup>
import { computed, ref } from 'vue';
  const bingoSize =ref(3)
  const bingoInputBox =ref()
  const bingoWidth = computed(() => {
    return (600 - 4*(bingoSize.value-1))/bingoSize.value
  })

  function changeTextHeight(idx) {
    let sh = bingoInputBox.value[idx].scrollHeight;
    if(bingoInputBox.value[idx].value == ''|| bingoInputBox.value[idx].value.length < 6){
      sh = 26;
    }
    bingoInputBox.value[idx].style.height = 'auto';
    bingoInputBox.value[idx].style.height = sh+'px';
  }

</script>
<template>
  <div>
    <div>
      빙고 사이즈
      <select name="size" id="size" v-model="bingoSize">
        <option :value="3">3×3</option>
        <option :value="4">4×4</option>
        <option :value="5">5×5</option>
      </select>
    </div>
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
