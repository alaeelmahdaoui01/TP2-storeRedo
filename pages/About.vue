<template>
    <div class="flex flex-col">
        <h1 class="font-bold text-center text-2xl about">About Us</h1>
        <div class="text-center text-lg text-gray-600"> 
            This is a demo store built with Nuxt.js and Tailwind CSS, showcasing modern web development
        practices and a beautiful user interface.
        </div>
    </div>
    
</template>

<style>
    .about{
        padding : 40px; 
    }
</style>

<script setup>
definePageMeta({
    layout:'default'
})
</script>
