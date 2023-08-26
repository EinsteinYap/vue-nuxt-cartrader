<template>
  <div>
    <header
      class="sticky top-0 z-50 flex justify-between items-center space-x-1 border-b bg white p-4 shadow-md"
    >
      <NuxtLink class="text-3xl font-mono" to="/">cartrader</NuxtLink>
      <div v-if="user" class="flex">
        <NuxtLink to="/profile/listings">Profile</NuxtLink>
        <p class="cursor-pointer mx-10" @click="logout">Logout</p>
      </div>
      <NuxtLink v-if="!user" to="/login">Login</NuxtLink>
    </header>
  </div>
</template>

<script setup>
const user = useSupabaseUser();
const supabase = useSupabaseClient();

// const logout = async () => {
//   const {error } = supabase.auth.signOut();
//   try {
//     await $fetch("api/_supabase/session", {
//       method: "POST",
//       body: { event: "SIGNED_OUT", session: null },
//     });
//   } catch (error) {
//     return console.log(error);
//   }
//   user.value = null;
//   navigateTo("/");
//   clearSupabaseCookies();
// };
// 3rd method
const logout = async () => {
  try {
    await supabase.auth.signOut();
    // clearAllSupabaseCookies();

    // navigateTo('/');
  } catch (error) {
    console.error(error);
  }
  // clearAllSupabaseCookies();
    navigateTo('/login');
};
const clearAllSupabaseCookies = () => {
  const cookies = document.cookie.split("; ");
  const supabaseCookiePrefix = "sb:"; // Adjust the prefix accordingly

  cookies.forEach((cookie) => {
    const [cookieName] = cookie.split("=");
    if (cookieName.startsWith(supabaseCookiePrefix)) {
      document.cookie = `${cookieName}=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/;`;
    }
  });
};
</script>
