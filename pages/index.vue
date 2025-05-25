<template>
  <div class="text-center py-20">
    <h1 class="text-4xl font-bold text-gray-800 py-5">Welcome to FakeStore</h1>
    <p class="text-xl text-gray-600 mb-8 ">Your one-stop shop for all your needs</p>
    <NuxtLink to="/Products" class="bg-blue-600 text-white px-6 py-3 rounded-lg text-lg hover:bg-blue-700">
      Browse Products
    </NuxtLink>
  </div>
</template>

<script setup>
definePageMeta({
  layout: 'default'
})
</script>
