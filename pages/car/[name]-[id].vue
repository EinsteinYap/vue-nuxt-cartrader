<template>
    <div v-if="car">
      <CarDetailHero :car="car" />
      <CarDetailAttributes :features="car.features" />
      <CarDetailDescription :description="car.description" />
      <CarDetailContact />
    </div>

</template>
<script setup>
const route = useRoute();
const {data:car } = await useFetch(`/api/car/${route.params.id}`)
const user =useSupabaseUser();
useHead({ 
  title:route.params.name 
    })
definePageMeta({
  layout:'custom'
});
onMounted =() =>{
  console.log('user Id ' , this.user)
}
</script>