<template>
    <div class="mt-10">
        <h1 class="text-5xl font-bold mb-7">
            <button class="bg-red-400 p-3 rounded text-white font-bold" @click="login">
                Login with Google
            </button>
        </h1>
    </div>
</template>

<script setup>
definePageMeta({
    layout:"custom"
});

const supabase = useSupabaseClient();
const user = useSupabaseUser();
const login =()=>{
    const {error} = supabase.auth.signInWithOAuth({
        provider:"google"
    })

    if(error){
        console.log(error)
    }
}
</script>