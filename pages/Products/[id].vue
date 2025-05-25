
<template>
    <div>
        <div v-if="error" class="text-center py-12">
            <p class="text-red-600">Error loading product details. Please try again later.</p>
        </div>
        <div v-else-if="product">
            <div class="max-w-4xl mx-auto bg-white rounded-lg shadow-lg overflow-hidden mt-20 mb-20">
                <div class="flex">
                    <div class="w-1/2 p-6">
                        <img :src="product.image" :alt="product.title" class="w-full h-96 object-contain" />
                    </div>
                    <div class="w-1/2 p-6">
                        <h1 class="text-3xl font-bold text-gray-800 mb-4">{{ product.title }}</h1>
                        <p class="text-gray-600 mb-4">{{ product.description }}</p>
                        <div class="mb-4">
                        <span class="text-2xl font-bold text-blue-600">${{ product.price }}</span>
                        <span class="ml-2 text-sm text-gray-500">Category: {{ product.category }}</span>
                        </div>
                        <div class="flex items-center mb-4">
                        <div class="flex items-center">
                            <span class="ml-1 text-gray-600">rating : {{ product.rating.rate}}</span>
                            <span class="ml-2 text-gray-500">({{ product.rating.count }} reviews)</span>
                        </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div v-else class="text-center py-12">
            <p class="text-gray-600">Product not found</p>
        </div>
    </div>
</template>

<script setup>
    definePageMeta({
        layout: 'default'
    })

    const route = useRoute()
    const { data: product, error } = await useFetch(`https://fakestoreapi.com/products/${route.params.id}`)


</script>

<style scoped>

</style>