<!-- the default layout for all pages -->

<template>
    <div class="min-h-screen flex flex-col">
        <nav >
            <div class="flex justify-between items-center navbar" >
                <NuxtLink class="font-bold navbari" to="/">FakeStore</NuxtLink>
                <div class="flex items-center space-x-4">
                    <NuxtLink class="navbari" to="/">Home</NuxtLink>
                    <NuxtLink class="navbari" to="/About">About</NuxtLink>
                    <NuxtLink class="navbari" to="/Products">Products</NuxtLink>
                </div>
            </div>
        </nav>

        <main class="flex-grow container mx-auto p-4">
            <slot/>
        </main>


        <footer >
            <div class="footer">
                <p>&copy; 2025 FakeStore. All rights reserved</p>
            </div>
        </footer>
    </div>

</template>

<style>
    .navbar{
        padding: 20px;
        background-color: rgb(67, 67, 138);
        font-size: 25px; 
        color: white;
    }
    .navbari:hover{
        color: rgb(166, 235, 166);
        cursor:pointer; 
    }
    .footer{
        background: #222;
        color: #fff;
        text-align: center;
        padding: 15px 0;
    }
    .router-link-exact-active {
        color: rgb(166, 235, 166);
    }
</style>