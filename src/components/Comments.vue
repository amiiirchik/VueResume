<script setup>
import { ref, inject } from 'vue'
import AppComment from './AppComment.vue'
const commentsApi = inject('commentsApi')    
let isLoad = ref(false)

const users = commentsApi.getComments()

function loadComments() {    
    if(!isLoad.value) {
        commentsApi.fetchComments()
        isLoad.value = true
    }
    else {
        isLoad.value = false
    }
}

</script>

<template>
    <div class="container">
        <button class="btn primary" :disabled="isLoad" @click="loadComments()" >Загрузить комментарии</button>
        <h2>Комментарии</h2>
        <app-comment v-if="isLoad" v-for="user in users" :key="user" :user="user" />
        <div  v-else class="loader"></div>
  </div>
</template>


<style lang="sass" scoped>
    h2
        color: white
</style>