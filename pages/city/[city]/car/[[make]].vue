<template>
    <div>
     <CarCards v-if="cars" :cars="cars"/>
     <h1 class="text-red-600" v-else>No Cars Found with Filters</h1>

    </div>
</template>

<script setup>
const route = useRoute();
    const {data:cars,refresh} =await useFetch(`/api/cars/${route.params.city}`,{
    mixPrice:route.query.mixPrice,
    maxPrice:route.query.maxPrice,
    make:route.params.make
});
watch(
    ()=>route.query,
    ()=>{
        window.location.reload(true);
    }
);
useHead({
    title:`Cars in ${route.params.city}`,
    
})
</script>