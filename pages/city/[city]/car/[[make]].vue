<template>
    <div>
     <CarCards />

    </div>
</template>

<script setup>
const route = useRoute();
useHead({
    
    title:`Cars in ${route.params.city}`,
    
    })
</script>