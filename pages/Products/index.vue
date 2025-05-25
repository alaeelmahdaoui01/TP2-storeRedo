<template>
    <div>
        <div class="flex gap-10 mb-6">
            <input
                v-model="searchquery"
                type="text"
                placeholder="Search products..."
                class="w-50 p-2 border rounded"
            />
            <select v-model="sortOrder" 
                class="px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500">
                <option value="">No sorting</option>
                <option value="price-asc">Price: Low to High</option>
                <option value="price-desc">Price: High to Low</option>
                <option value="name-asc">Name: A to Z</option>
                <option value="name-desc">Name: Z to A</option>
            </select>
        </div>

        <div v-if="error">
            Error loading products. please try again later. 
        </div>
        <div v-else-if="filteredproducts.length===0">
            No products found.
        </div>
        <div v-else>
            <div class="grid grid-cols-3 gap-6 mb-10">
                <div v-for="product in filteredproducts" :key="product.id">
                    <div class="bg-white rounded shadow flex flex-col ">
                        <!-- object contain, to make the image in its right proportions  
                         w-50 h-50 its for width and height -->
                        <img :src="product.image" :alt="product.title" class="w-50 h-50 object-contain p-4" />
                        <div class="p-4 flex flex-col justify-between">
                            <div>
                                <!-- line-clamp  to show how many lines of the text -->
                                 <!-- px py padding on x or y and mb: margin bottom  -->
                                <h3 class="text-lg font-semibold text-gray-800 mb-2 line-clamp-1">{{ product.title }}</h3>
                                <p class="text-gray-600 mb-2 line-clamp-2">{{ product.description }}</p>
                            </div>
                            <div class="flex justify-between items-center mt-4">
                                <span class="text-xl font-bold text-blue-600">${{ product.price }}</span>
                                <NuxtLink :to="'/Products/' + product.id" class="bg-blue-600 text-white hover:bg-blue-800 px-4 py-2 rounded">
                                View Details
                                </NuxtLink>
                            </div>
                        </div>
                    </div>
                </div>

            </div>
            
        </div>

    </div>
</template>

<script setup>

definePageMeta({
    layout:'default'
})
const {data: products, error }= await useFetch('https://fakestoreapi.com/products/')


// products have id, title, description, image, and price 

const searchquery = ref('')
const filteredproducts=computed(()=>{
    let result = [...products.value]  // list of all products 
    if (searchquery.value){
        const query = searchquery.value.toLowerCase()
        result = result.filter(product => 
            product.title.toLowerCase().includes(query)) ||
            product.description.toLowerCase().includes(query)
    }
    return result
})
</script>