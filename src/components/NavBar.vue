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
        <div class="navBox">
            <RouterLink to="/">Home</RouterLink>
            <RouterLink to="/make">빙고 만들기</RouterLink>
        </div>
        <div class="searchBox d-flex">
            <input type="text" placeholder="키워드 또는 빙고아이디로 검색해보세요" ref="txtSearch" @keyup.enter="search()">
            <button @click="search()">검색</button>
        </div>
    </div>
</template>
<style>
.navBox{
    flex-grow: 1;
}
.searchBox{
    width:300px;
    gap: 8px;

}
</style>