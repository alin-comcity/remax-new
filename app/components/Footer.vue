<script setup></script>

<style scoped>
.font-display {
  font-family: "Nunito", sans-serif;
  color: white;
}
</style>

<template>
  <div class="grid grid-flow-row font-display pt-8">
    <div
      class="grid lg:grid-flow-col lg:grid-cols-4 px-8 py-12 grid-cols-1 gap-4 bg-[#2D363F]"
    >
      <div class="col-span-1">
        <NuxtLink to="/">
          <NuxtImg src="/remax-logo.png" class="h-8" />
        </NuxtLink>
      </div>
      <div class="col-span-1">
        <ul>
          <li class="p-2 text-white">Services</li>
          <li class="text-xm p-2">
            <NuxtLink to="/blog" class="hover:text-white">Blog</NuxtLink>
          </li>
          <li class="text-xm p-2">
            <NuxtLink to="/about" class="hover:text-white">About</NuxtLink>
          </li>
          <li class="text-xm p-2">
            <NuxtLink to="/terms" class="hover:text-white"
              >Privacy Policy</NuxtLink
            >
          </li>
        </ul>
      </div>

      <div class="col-span-1">
        <ul>
          <li class="p-2 text-white">Company</li>
          <!-- <li class="text-xm p-2">
                        <NuxtLink to="/whatwedo" class="hover:text-white">What We Do</NuxtLink>
                    </li> -->
          <li class="text-xm p-2">
            <NuxtLink to="/faq" class="hover:text-white">FAQs</NuxtLink>
          </li>
          <!-- <li class="text-xm p-2">
                        <NuxtLink to="/latestpost" class="hover:text-white">Latest Posts</NuxtLink>
                    </li> -->
          <!-- <li class="text-xm p-2">
            <NuxtLink to="/contact" class="hover:text-white">Contact</NuxtLink>
          </li> -->
        </ul>
      </div>

      <!-- Form Section -->
      <div class="col-span-1">
        <p class="leading-normal my-5"></p>
      </div>
    </div>

    <div
      class="p-8 grid lg:grid-flow-col lg:grid-cols-2 grid-cols-1 border-t border-white bg-[#1B1F23]"
    >
      <div class="col-span-1 flex items-center gap-3">
        <div></div>
        <div></div>
      </div>

      <div class="col-span-1 lg:text-right">
        <p class>© Copyright 2026 Remax BD</p>
      </div>
    </div>
  </div>
</template>
