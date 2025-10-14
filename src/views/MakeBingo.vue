<script setup>
import { computed, ref } from 'vue';
const bingoSize =ref(3)
const bingoTitle = ref('')
const bingoInputBox =ref()
const bingoWidth = computed(() => {
  return (600 - 4*(bingoSize.value-1))/bingoSize.value
})

function changeTextHeight(idx) {
  let sh = bingoInputBox.value[idx].scrollHeight;
  if(bingoInputBox.value[idx].value == ''|| bingoInputBox.value[idx].value.length < 6){
    sh = 37;
  }
  bingoInputBox.value[idx].style.height = 'auto';
  bingoInputBox.value[idx].style.height = sh+'px';
}

function isNull(value) {
  return value === null || value === undefined
}

function saveCommand() {
  const btitle = bingoTitle.value
  const bsize = bingoSize.value
  const bvalues = bingoInputBox.value.map(e => {
    return isNull(e.value) ? '' : e.value
  })
  return {title: btitle, size:bsize, values:bvalues}

}

function resetCommand() {
  for(let i=0; i<bingoInputBox.value.length;i++){
    bingoInputBox.value[i].value = ''
  }
}

</script>
<template>
  <div>
    <div class="bingoSetting d-flex">
      <div class="bingoTitle d-flex">
        <label for="title">
          빙고 제목
        </label>
        <input type="text" name="" id="title" v-model="bingoTitle">
      </div>
      <div class="bingoSize d-flex">
        <label for="size">
          빙고 크기
        </label>
        
        <select class="bingoSizeCombo" name="size" id="size" v-model="bingoSize">
          <option :value="3">3×3</option>
          <option :value="4">4×4</option>
          <option :value="5">5×5</option>
        </select>
      </div>
      <!-- <div class="bingoTag d-flex">
        <label for="tag">태그</label>
        <input type="text">
      </div> -->
    </div>
    <div class="bingoArea" :style="`grid: repeat(${bingoSize}, 1fr) / repeat(${bingoSize}, 1fr);`">
      <div class="bingoCell" :style="`width: ${bingoWidth}px; height: ${bingoWidth}px;`" v-for="row in Math.pow(bingoSize,2)" :key="row">
        <textarea :style="`width: ${bingoWidth-3}px;`" ref="bingoInputBox" rows="1" class="bingoInput" @keyup="changeTextHeight(row-1)"></textarea>
      </div>
    </div>
    <div>
      <button @click="saveCommand">저장</button>
      <button @click="resetCommand">리셋</button>
    </div>
  </div>
</template>

<style>
.bingoSetting{
  font-size: 1.2rem;
  flex-direction: column;
  gap: 6px;
  margin-bottom: 12px;
}
.bingoSetting label{
  width: 100px;
}
.bingoSetting input[type=text]{
  border: 1px solid steelblue;
  border-radius: 4px;
  padding: 2px 4px;
}

.bingoSizeCombo{
  border:1px solid steelblue;
  border-radius: 4px;
  padding: 2px 4px;
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
  border-radius: 16px;
  padding: 16px 0;
}
.bingoInput{
  background: none;
  outline: none;
  border: 1px solid transparent;
  font-size: 1.5rem;
  font-family: 'Escoredream';
  text-align: center;
  resize: none;
  overflow: hidden;
}
</style>
