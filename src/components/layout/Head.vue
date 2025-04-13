<template>
    <nav class="bg-white shadow">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex justify-between h-16">
          <!-- Logo -->
          <div class="flex-shrink-0 flex items-center">
            <RouterLink to="/"
              ><img class="w-3xs" :src="logo" alt="it's a logo of hoppy co"
            /></RouterLink>
          </div>
  
          <!-- Desktop Navigation -->
          <div class="hidden md:flex items-center space-x-4">
            <router-link
              v-for="item in navItems"
              :key="item.path"
              :to="item.path"
              class="px-3 py-2 text-gray-700 hover:text-indigo-600"
            >
              {{ item.label }}
            </router-link>
          </div>
  
          <!-- Mobile Hamburger Button -->
          <div class="md:hidden flex items-center">
            <button
              @click="toggleMobileMenu"
              class="text-gray-500 hover:text-gray-600 focus:outline-none"
            >
              <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M4 6h16M4 12h16M4 18h16"
                />
              </svg>
            </button>
          </div>
        </div>
      </div>
  
      <!-- Mobile Menu -->
      <div v-if="mobileMenuOpen" class="md:hidden">
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
  </template>
  
  <script setup lang="ts">
  import { ref } from "vue";
  import logo from "@/assets/img/logo.png";
  
  const mobileMenuOpen = ref(false);
  const navItems = [
    { path: "/", label: "nav.home" },
    { path: "/about", label: "nav.about" },
    // Other nav items
  ];
  
  const toggleMobileMenu = () => {
    mobileMenuOpen.value = !mobileMenuOpen.value;
  };
  </script>
  