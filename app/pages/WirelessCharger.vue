<script setup>
const { data: products } = await useFetch(
  "https://admindash.comcitybd.com/api/brands/Remax/60",
  {
    query: {
      "id[]": [113],
    },
    transform: (res) => res.data,
    default: () => [],
    server: false,
  },
);
</script>

<style scoped>
.font-display {
  font-family: "Nunito", sans-serif;
  color: #333;
}
</style>

<template>
  <div class="font-display py-16">
    <div class="text-center text-3xl font-light">
      <h2>Wireless Charger</h2>
    </div>
    <div class="container mx-auto">
      <div
        class="grid lg:grid-cols-4 grid-cols-1 gap-6 px-6 py-12"
        v-if="products != null"
      >
        <div
          class="hover:shadow-2xl shadow-lg hover:-translate-y-2 hover:transition hover:duration-1000 duration-1000"
          v-for="product in products"
          :key="product.slug"
        >
          <NuxtLink :to="`/product/${product.slug}`">
            <NuxtImg :src="product.photo" :alt="product.name" />
            <p class="text-rongtatext text-sm font-semibold px-8 py-2">
              {{ product.name }}
            </p>
          </NuxtLink>
        </div>
      </div>
    </div>
  </div>
</template>
