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
        <div class="searchBox">
            <input type="text" placeholder="키워드 또는 빙고아이디로 검색해보세요" class="txtSearchBox" ref="txtSearch" @keyup.enter="search()">
            <button class="searchButton" @click="search()">검색</button>        </div>
    </div>
</template>
<style>
.navBox{
    flex-grow: 1;
    gap: 12px;
}
.searchBox{
    width:340px;
    position: relative;
}

.txtSearchBox{
    width: 100%;
    padding:8px 32px 8px 12px;
    border-radius: 20px;
    border: 1px solid steelblue;
}
.searchButton{
    position: absolute;
    top: 4px;
    right: 8px;
    background: none;
    outline: none;
    border: 0;
}
</style>