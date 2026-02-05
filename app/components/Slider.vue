<script setup>
const images = ref(["/slider-one.jpg", "/slider-two.jpg", "/slider-three.jpg"]);

const currentIndex = ref(0);
let timer = null;

onMounted(() => {
  startSlide();
});

const startSlide = () => {
  timer = setInterval(next, 10000);
};

const next = () => {
  currentIndex.value += 1;
};

const prev = () => {
  currentIndex.value -= 1;
};

const currentImg = computed(() => {
  return images.value[Math.abs(currentIndex.value) % images.value.length];
});
</script>

<style scoped>
.font-display {
  font-family: "Nunito", sans-serif;
  color: #333;
}
</style>

<template>
  <div class="font-display h-52 lg:h-[600px] 2xl:h-[900px]">
    <div class="absolute">
      <div v-for="i in [currentIndex]" :key="i">
        <NuxtImg :src="currentImg" />

        <!-- <div class="">
                    <a class="prev" @click="prev" href="#">&#10094; Previous</a>
                    <a class="next" @click="next" href="#">&#10095; Next</a>
                </div> -->
      </div>
    </div>
  </div>
</template>
