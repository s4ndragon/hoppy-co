<script setup lang="ts">
import { ref } from "vue";
import logo from "@/assets/img/logo.png";

const mobileMenuOpen = ref(false);
const navItems = [
  { path: "/our-beverages", label: "Beverages" },
  { path: "/about", label: "About" },
  { path: "/events", label: "Events" },
  { path: "/faqs", label: "FAQs" },
];

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value;
};
</script>
<template>
  <header class="h-24 flex justify-between items-center px-8 py-4 header">
    <!-- logo -->
    <RouterLink to="/">
      <h1>
        <img class="w-3xs" :src="logo" alt="it's a logo of hoppy co" />
      </h1>
    </RouterLink>

    <nav class="w-2/3 h-full flex md:justify-between justify-end items-center">
      <!-- desktop nav -->
      <div class="w-full hidden md:flex justify-between text-3xl">
        <RouterLink v-for="item in navItems" :key="item.path" :to="item.path">{{
          item.label
        }}</RouterLink>
      </div>

      <!-- Mobile Hamburger Button -->
      <div class="md:hidden fixed items-center">
        <button
          @click="toggleMobileMenu"
          class="text-gray-500 hover:text-gray-600 focus:outline-none"
        >
          <svg class="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="white">
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 6h16M4 12h16M4 18h16"
            />
          </svg>
        </button>
      </div>

      <!-- Mobile Menu -->
      <div v-if="mobileMenuOpen" class="md:hidden" :class="{ open: toggleMobileMenu }">
        <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
          <router-link
            v-for="item in navItems"
            :key="item.path"
            :to="item.path"
            class="block px-3 py-2 text-gray-700 hover:text-indigo-600"
          >
            {{ item.label }}
          </router-link>
        </div>
      </div>
    </nav>
  </header>
</template>
<style lang="scss">
.header {
  font-family: "Baloo Tamma 2", system-ui;
  font-optical-sizing: auto;
  font-weight: 900;
  font-style: normal;
}

@media only screen and (max-width: 768px) {
  //   nav {
  //     display: none;
  //   }
  .open {
    display: fixed;
    flex-direction: column;
    -webkit-clip-path: circle(50px at 120% -10%);
    transition: all 1s ease-out;
    width: 100%;
    height: 100vh;
  }
}
</style>
