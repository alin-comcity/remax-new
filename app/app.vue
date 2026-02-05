<script setup>
const router = useRouter();
const nuxtApp = useNuxtApp();

function searchs(event) {
  console.log(event);
  router.push(`/search/${event}`);
}

onMounted(() => {
  nuxtApp.$on?.("customSearch", (event) => {
    searchs(event);
  });
});
</script>

<style scoped>
.font-display {
  font-family: "Nunito", sans-serif;
}

@media (max-width: 768px) {
  .hidemobile {
    display: none;
  }
}

@media (min-width: 768px) {
  .hidedesktop {
    display: none;
  }
}
</style>

<template>
  <div>
    <MobileHeader class="hidedesktop" @custom-search="searchs" />
    <Header class="hidemobile" @custom-search="searchs" />
    <NuxtPage />
    <Footer />
  </div>
</template>
