<script setup>
const route = useRoute();
const query = ref(route.params.data);
const products = ref([]);
// Function to fetch search results
async function fetchProducts(slug) {
  const { data, error, refresh } = await useFetch(
    `https://admindash.comcitybd.com/api/customsearch/Remax/${query.value}`,
  );

  if (error.value) {
    console.error("API Error:", error.value);
    products.value = [];
  } else {
    products.value = data.value?.data || [];
  }

  return refresh;
}

let refreshFn = await fetchProducts(query.value);
console.log(refreshFn);
</script>

<style scoped>
.font-display {
  font-family: "Nunito", sans-serif;
  color: #333;
}
</style>

<template>
  <div class="container mx-auto font-display py-16">
    <h3 class="px-6 font-semibold uppercase mt-8">
      Search Result For "{{ query }}"
    </h3>

    <div
      class="grid lg:grid-cols-4 grid-cols-1 gap-6 px-6 py-12"
      v-if="products != null"
    >
      <div
        class="hover:shadow-2xl shadow-lg hover:-translate-y-2 hover:transition hover:duration-1000 duration-1000"
        v-for="product in products"
        :key="product.slug"
      >
        <nuxt-link :to="`/product/${product.slug}`">
          <NuxtImg :src="product.thumbnail" alt="Casing" class="w-full" />
          <p class="text-rongtatext text-sm font-semibold px-8 py-2">
            {{ product.name }}
          </p>
        </nuxt-link>
      </div>
    </div>
  </div>
</template>
