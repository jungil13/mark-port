<script setup>
import { ref, computed } from "vue";
import { useRoute, RouterLink, RouterView } from "vue-router";

const isMobileMenuOpen = ref(false);
const route = useRoute();

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
};

// Function to determine if a link is active
const isActive = (to) => {
  return to === route.path;
};
</script>

<template>
  <header class="bg-white text-white py-8 border border-shadow-gray">
    <div class="container mx-auto flex items-center justify-between">
      <RouterLink to="/" class="flex items-center">
        <span class="text-2xl font-bold font-sans ml-4 text-black">Mark.</span>
      </RouterLink>

      <!-- Mobile Menu Button -->
      <button
        @click="toggleMobileMenu"
        class="block sm:hidden text-black focus:outline-none"
      >
        <svg
          class="h-10 w-10"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M4 6h16M4 12h16m-7 6h7"
          ></path>
        </svg>
      </button>

      <!-- Mobile Drawer -->
      <div
        v-if="isMobileMenuOpen"
        class="absolute inset-x-0 top-0 p-4 bg-white text-center border border-red-800"
      >
        <nav class="flex flex-col space-y-4">
          <RouterLink
            to="/"
            :class="{ 'active-nav-link': isActive('/') }"
            class="text-black nav-link font-semibold text-xl"
            @click="toggleMobileMenu"
            >Home</RouterLink
          >
          <RouterLink
            to="/project"
            :class="{ 'active-nav-link': isActive('/project') }"
            class="text-black nav-link font-semibold text-xl"
            @click="toggleMobileMenu"
            >Project</RouterLink
          >
          <RouterLink
            to="/contact"
            :class="{ 'active-nav-link': isActive('/contact') }"
            class="text-black nav-link font-semibold text-xl"
            @click="toggleMobileMenu"
            >Contact</RouterLink
          >
          <RouterLink
            to="/about"
            :class="{ 'active-nav-link': isActive('/about') }"
            class="text-black nav-link font-semibold text-xl"
            @click="toggleMobileMenu"
            >About</RouterLink
          >
        </nav>
      </div>

      <!-- Navigation -->
      <nav class="hidden sm:block">
        <RouterLink
          to="/"
          :class="{ 'active-nav-link': isActive('/') }"
          class="text-black nav-link font-semibold text-xl"
          >Home</RouterLink
        >
        <RouterLink
          to="/project"
          :class="{ 'active-nav-link': isActive('/project') }"
          class="text-black nav-link font-semibold text-xl"
          >Project</RouterLink
        >
        <RouterLink
          to="/contact"
          :class="{ 'active-nav-link': isActive('/contact') }"
          class="text-black nav-link font-semibold text-xl"
          >Contact</RouterLink
        >
        <RouterLink
          to="/about"
          :class="{ 'active-nav-link': isActive('/about') }"
          class="text-black nav-link font-semibold text-xl"
          >About</RouterLink
        >
      </nav>
    </div>
  </header>

  <RouterView />
  <!-- footer -->
  <footer
    id="foot"
    class="fixed bottom-0 left-0 w-full bg-white border border-shadow-gray text-white py-2 text-center"
  >
    <span
      class="block text-sm text-black sm:text-center dark:text-black font-semibold"
      >© 2024
      <a href="https://flowbite.com/" class="hover:underline">Portfolio™</a>.
      All Rights Reserved - Created by: Mark Jayson.</span
    >
  </footer>
</template>

<style scoped>
.nav-link {
  padding: 0.5rem 1rem;
  transition: background-color 0.3s ease;
}

.nav-link:hover {
  background-color: rgba(255, 255, 255, 0.1);
}

/* Style for active navigation link */
.active-nav-link {
  border-bottom: 2px solid rgb(0, 0, 0);
}
</style>
