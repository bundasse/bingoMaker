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
    <div class="bingoArea">
      <div v-for="col in bingoSize" :key="col" class="bingoCol">
        <div class="bingoCell" v-for="row in bingoSize" :key="row">
          <input type="text" name="" id="" class="bingoInput">
        </div>
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
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.bingoCol{
  display: flex;
  gap: 8px;
}
.bingoCell{
  flex-grow: 1;
  height: 50px;
  align-items: stretch;
  background-color: none;
  border: 1px solid steelblue;
  border-radius: 8px;
  padding: 8px 0;
}
.bingoInput{
  background: none;
  outline: none;
  border: 0;
  padding: 4px;
  border-radius: 4px;
}
.bingoInput:focus{
  border: 1px solid lightblue;
}
</style>
