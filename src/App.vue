<script>
import { RouterView } from "vue-router";
import Hero from "./components/Hero.vue";
import navbar from "./components/Navbar.vue";

export default {
  components: {
    navbar,
    Hero,
  },
};
</script>

<template>
  <header>
    <navbar></navbar>
  </header>
  <main class="container">
    <Hero></Hero>
    <RouterView></RouterView>
  </main>
</template>
