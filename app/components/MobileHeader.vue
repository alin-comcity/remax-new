<script setup>
const showMenu = ref(false);
const showSearch = ref(false);
const query = ref("");

const openCategory = ref("");

const toggleMenu = () => (showMenu.value = !showMenu.value);
const toggleSearch = () => (showSearch.value = !showSearch.value);
const toggleCategory = (category) => {
  openCategory.value = openCategory.value === category ? "" : category;
};
const submitSearch = () => {
  console.log("Search query:", query.value);
};
</script>

<style scoped>
.font-display {
  font-family: "Nunito", sans-serif;
}

.offcanvas-overlay {
  position: fixed;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 40;
}
</style>

<template>
  <div class="font-display">
    <!-- Navbar -->
    <div class="grid grid-cols-6 bg-black h-12 items-center relative z-50">
      <!-- Logo -->
      <div class="col-span-4 flex items-center pl-4">
        <NuxtLink to="/">
          <img src="/remax-logo.png" class="h-6" />
        </NuxtLink>
      </div>

      <!-- Search icon -->
      <div class="col-span-1 flex justify-end items-center">
        <img
          src="/search.png"
          class="h-6 w-6 cursor-pointer"
          @click="toggleSearch"
        />
      </div>

      <!-- Search input -->
      <transition
        enter-active-class="transition ease-out duration-300"
        enter-from-class="transform opacity-0 scale-95"
        enter-to-class="transform opacity-100 scale-100"
        leave-active-class="transition ease-in duration-200"
        leave-from-class="transform opacity-100 scale-100"
        leave-to-class="transform opacity-0 scale-95"
      >
        <div
          v-if="showSearch"
          class="absolute top-12 right-12 z-50 bg-white p-2 rounded shadow"
        >
          <form class="inline-flex" @submit.prevent="submitSearch">
            <input
              type="text"
              placeholder="Keyword.."
              v-model="query"
              class="py-1 px-2 border border-gray-400 rounded text-sm"
            />
            <button
              type="submit"
              class="bg-[#fdd000] text-white px-2 py-1 text-sm"
            >
              Search
            </button>
          </form>
        </div>
      </transition>

      <!-- Hamburger menu -->
      <div class="col-span-1 flex justify-center items-center">
        <button type="button" @click="toggleMenu">
          <img src="/ham.png" class="h-6 cursor-pointer" />
        </button>
      </div>
    </div>

    <!-- Offcanvas overlay -->
    <div v-if="showMenu" class="offcanvas-overlay" @click="toggleMenu"></div>

    <!-- Offcanvas menu -->
    <transition
      enter-active-class="transition-transform duration-300"
      enter-from-class="translate-x-full"
      enter-to-class="translate-x-0"
      leave-active-class="transition-transform duration-300"
      leave-from-class="translate-x-0"
      leave-to-class="translate-x-full"
    >
      <div
        v-if="showMenu"
        class="fixed top-0 right-0 z-50 h-full w-72 bg-white shadow-lg overflow-y-auto"
      >
        <div class="flex justify-between items-center p-4 border-b">
          <h2 class="font-semibold text-lg">Product Categories</h2>
          <button @click="toggleMenu" class="text-black font-bold text-xl">
            ✕
          </button>
        </div>

        <!-- Menu items -->
        <div class="p-4 space-y-4">
          <!-- Creative Lifestyle -->
          <div>
            <h3
              @click="toggleCategory('CreativeLifestyle')"
              class="font-medium mb-2 cursor-pointer flex justify-between items-center"
            >
              Creative Lifestyle
              <span>{{
                openCategory === "CreativeLifestyle" ? "▲" : "▼"
              }}</span>
            </h3>

            <transition
              enter-active-class="transition max-h-96 duration-300 ease-out overflow-hidden"
              enter-from-class="max-h-0"
              enter-to-class="max-h-96"
              leave-active-class="transition max-h-96 duration-300 ease-in overflow-hidden"
              leave-from-class="max-h-96"
              leave-to-class="max-h-0"
            >
              <ul
                v-if="openCategory === 'CreativeLifestyle'"
                class="space-y-1 pl-2"
              >
                <NuxtLink to="/selfiestick">
                  <li
                    class="px-4 py-2 border rounded hover:bg-gray-100 cursor-pointer"
                  >
                    Selfie Stick
                  </li>
                </NuxtLink>
                <NuxtLink to="/laptopbag">
                  <li
                    class="px-4 py-2 border rounded hover:bg-gray-100 cursor-pointer"
                  >
                    Laptop Bag
                  </li>
                </NuxtLink>
              </ul>
            </transition>
          </div>

          <!-- Audio -->
          <div>
            <h3
              @click="toggleCategory('Audio')"
              class="font-medium mb-2 cursor-pointer flex justify-between items-center"
            >
              Audio
              <span>{{ openCategory === "Audio" ? "▲" : "▼" }}</span>
            </h3>

            <transition
              enter-active-class="transition max-h-96 duration-300 ease-out overflow-hidden"
              enter-from-class="max-h-0"
              enter-to-class="max-h-96"
              leave-active-class="transition max-h-96 duration-300 ease-in overflow-hidden"
              leave-from-class="max-h-96"
              leave-to-class="max-h-0"
            >
              <ul v-if="openCategory === 'Audio'" class="space-y-1 pl-2">
                <NuxtLink to="/bluetoothspeaker">
                  <li
                    class="px-4 py-2 border rounded hover:bg-gray-100 cursor-pointer"
                  >
                    Bluetooth Speaker
                  </li>
                </NuxtLink>
                <NuxtLink to="/wiredheadphone">
                  <li
                    class="px-4 py-2 border rounded hover:bg-gray-100 cursor-pointer"
                  >
                    Wired Headphone & Earphone
                  </li>
                </NuxtLink>
                <NuxtLink to="/btheadphone">
                  <li
                    class="px-4 py-2 border rounded hover:bg-gray-100 cursor-pointer"
                  >
                    BT Headphone & Earphone
                  </li>
                </NuxtLink>
                <NuxtLink to="/voicerecorder">
                  <li
                    class="px-4 py-2 border rounded hover:bg-gray-100 cursor-pointer"
                  >
                    Voice Recorder
                  </li>
                </NuxtLink>
                <NuxtLink to="/microphone">
                  <li
                    class="px-4 py-2 border rounded hover:bg-gray-100 cursor-pointer"
                  >
                    Microphone
                  </li>
                </NuxtLink>
              </ul>
            </transition>
          </div>

          <!-- Protection -->
          <div>
            <h3
              @click="toggleCategory('Protection')"
              class="font-medium mb-2 cursor-pointer flex justify-between items-center"
            >
              Protection
              <span>{{ openCategory === "Protection" ? "▲" : "▼" }}</span>
            </h3>

            <transition
              enter-active-class="transition max-h-96 duration-300 ease-out overflow-hidden"
              enter-from-class="max-h-0"
              enter-to-class="max-h-96"
              leave-active-class="transition max-h-96 duration-300 ease-in overflow-hidden"
              leave-from-class="max-h-96"
              leave-to-class="max-h-0"
            >
              <ul v-if="openCategory === 'Protection'" class="space-y-1 pl-2">
                <NuxtLink to="/mobilecase">
                  <li
                    class="px-4 py-2 border rounded hover:bg-gray-100 cursor-pointer"
                  >
                    Mobile Case
                  </li>
                </NuxtLink>
              </ul>
            </transition>
          </div>

          <!-- Energy -->
          <div>
            <h3
              @click="toggleCategory('Energy')"
              class="font-medium mb-2 cursor-pointer flex justify-between items-center"
            >
              Energy
              <span>{{ openCategory === "Energy" ? "▲" : "▼" }}</span>
            </h3>

            <transition
              enter-active-class="transition max-h-96 duration-300 ease-out overflow-hidden"
              enter-from-class="max-h-0"
              enter-to-class="max-h-96"
              leave-active-class="transition max-h-96 duration-300 ease-in overflow-hidden"
              leave-from-class="max-h-96"
              leave-to-class="max-h-0"
            >
              <ul v-if="openCategory === 'Energy'" class="space-y-1 pl-2">
                <NuxtLink to="/usbhub">
                  <li
                    class="px-4 py-2 border rounded hover:bg-gray-100 cursor-pointer"
                  >
                    USB Hub
                  </li>
                </NuxtLink>
                <NuxtLink to="/wirelesscharger">
                  <li
                    class="px-4 py-2 border rounded hover:bg-gray-100 cursor-pointer"
                  >
                    Wireless Charger
                  </li>
                </NuxtLink>
                <NuxtLink to="/powerstrip">
                  <li
                    class="px-4 py-2 border rounded hover:bg-gray-100 cursor-pointer"
                  >
                    Power Strip
                  </li>
                </NuxtLink>
                <NuxtLink to="/usbcharger">
                  <li
                    class="px-4 py-2 border rounded hover:bg-gray-100 cursor-pointer"
                  >
                    USB/PD Charger
                  </li>
                </NuxtLink>
                <NuxtLink to="/carcharger">
                  <li
                    class="px-4 py-2 border rounded hover:bg-gray-100 cursor-pointer"
                  >
                    Car Charger
                  </li>
                </NuxtLink>
                <NuxtLink to="/powerbank">
                  <li
                    class="px-4 py-2 border rounded hover:bg-gray-100 cursor-pointer"
                  >
                    Power Bank
                  </li>
                </NuxtLink>
                <NuxtLink to="/chargingcable">
                  <li
                    class="px-4 py-2 border rounded hover:bg-gray-100 cursor-pointer"
                  >
                    Data & Charging Cable
                  </li>
                </NuxtLink>
              </ul>
            </transition>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>
