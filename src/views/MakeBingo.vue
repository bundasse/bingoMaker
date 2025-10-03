<script setup>
import { ref } from 'vue';
  const bingoSize =ref(3)

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
    <div class="bingoArea" :style="`grid-template-rows: repeat(${bingoSize}, 1fr); grid-template-columns: repeat(${bingoSize}, 1fr);`">
      <div class="bingoCell" v-for="row in Math.pow(bingoSize,2)" :key="row">
        <input type="text" class="bingoInput">
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
  border:1px solid red;
  display: grid;
  gap: 8px;
}
.bingoCell{
  align-items: stretch;
  background-color: none;
  border: 1px solid steelblue;
  border-radius: 20px;
  padding: 20px 0;
}
.bingoInput{
  background: none;
  outline: none;
  border: 1px solid transparent;
  font-size: 2rem;
  padding: 4px;
  border-radius: 4px;
}
.bingoInput:focus{
  border: 1px solid lightblue;
}
</style>
