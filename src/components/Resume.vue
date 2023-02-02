<script setup>
const props = defineProps({
    title: String,
    subtitle: String,
    avatar: String,
    text: String
})

</script>

<template>
     <div class="card card-w70">
        <h1>Резюме {{ title }}</h1>
        <div class="avatar">
            <img :src="avatar">
        </div>
        <h2>{{ subtitle }}</h2>
        <p>{{ text }}</p>
    </div>
</template>