<script setup>
import Comments from './components/Comments.vue';
import AppForm from './components/AppForm.vue';

import { provide} from 'vue'
import {commentsApi} from './api/api'

const api = commentsApi()
provide('commentsApi', api)

</script>


<template>
  <div class="container column">
    <AppForm />
  </div>
  <Comments />
</template>

<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
</style>
