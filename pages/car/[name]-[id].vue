<template>
    <div v-if="car">
      <CarDetailHero :car="car" />
      <CarDetailAttributes :features="car.features" />
      <CarDetailDescription :description="car.description" />
      <CarDetailContact />
    </div>

</template>
<script setup>
const {cars} =useCars();
const route = useRoute();
const car = computed(()=>{
  return cars.find((c)=>{
    return c.id === parseInt(route.params.id)
  })
});

if(!car.value){
  throw createError({
    statusCode:404,
    message:`Car with ID of ${route.params.id} does not exits`
  })
}
useHead({ 
  title:route.params.name 
    })
definePageMeta({
  layout:'custom'
});
</script>