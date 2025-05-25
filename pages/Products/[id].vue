<template>
    <div v-if=product>
        <img :src=product.image>
        <div> {{ product.title}}</div>
        <div> {{ product.description }}</div>
        <div> {{ product.price }} </div>
    </div>
</template>

<script setup>
definePageMeta({
    layout:'default'
})
const {data: products, error }= await useFetch(`https://fakestoreapi.com/products/${route.params.id}`)

</script>