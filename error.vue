<template>
<div class="flex flex-col justify-center items-center h-screen">
    <div class="flex flex-col justify-center items-center">
        <h1 class="text-5xl">{{ error.statusCode }}</h1>
        <h1 class="text-9xl">{{ error.message }}</h1>
    </div>
    <div>
        <button class="rounded mt-7 text-2xl bg-blue-400 px-7 py-4 text-white" @click="handleError">Go Back</button>
    </div>
</div>
   
</template>
<script setup>
const error =useError();
const handleError =() =>{
 navigateTo('/')
}
</script>