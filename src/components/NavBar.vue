<script setup>
import router from '@/router';
import { ref, onMounted, defineEmits } from 'vue';
import { RouterLink } from 'vue-router'

const emits = defineEmits('search')
const txtSearch=ref()

function search() {
    router.go('/');
    let searchTxt = txtSearch.value.value;
    emits('search',searchTxt);
}

onMounted(() => {
    txtSearch.value.value = '';
})
</script>
<template>
    <div class="d-flex">
        <div class="navBox d-flex">
            <RouterLink to="/">Home</RouterLink>
            <RouterLink to="/make">빙고 만들기</RouterLink>
        </div>
        <div class="searchBox d-flex">
            <input type="text" placeholder="키워드 또는 빙고아이디로 검색해보세요" ref="txtSearch" @keyup.enter="search()" style="width:260px;">
            <button @click="search()">검색</button>
        </div>
    </div>
</template>
<style>
.navBox{
    flex-grow: 1;
    gap: 12px;
}
.searchBox{
    width:320px;
    gap: 8px;
    justify-content: end;
}
</style>