<script setup>
import { ref } from "vue";
import Navbar from "./components/Navbar.vue";
import Home from "./components/Home.vue";
import Information from "./components/Information.vue";
import AboutUs from "./components/AboutUs.vue";
import ToastNotification from "./components/ToastNotification.vue";

// Define a simple routing system with ref
const currentPage = ref("home");
const dismissedPages = ref(new Set());

function goToPage(page) {
  currentPage.value = page;
}

function dismissToast(page) {
  dismissedPages.value.add(page);
}
</script>

<template>
  <div>
    <Navbar :navigate="goToPage" :currentPage="currentPage" /> <!-- Pass currentPage to Navbar -->
    
    <main>
      <Home v-if="currentPage === 'home'" />
      <Information v-if="currentPage === 'information'" />
      <AboutUs v-if="currentPage === 'aboutUs'" />
    </main>

    <ToastNotification
      v-if="!dismissedPages.has(currentPage)"
      @dismiss="dismissToast(currentPage)"
    />
  </div>
</template>

<style scoped>
main {
  padding: 20px;
  font-family: Arial, sans-serif;
  color: white;
}
</style>
