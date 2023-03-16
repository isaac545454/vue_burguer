<template>
  <Navbar />
  <router-view />
  <Footer />
</template>

<script>
import Navbar from "./components/NabarHeader.vue";
import Footer from "./components/FooterHeader.vue";

export default {
  components: {
    Navbar,
    Footer,
  },
};
</script>

<!-- <style>
nav a.router-link-exact-active {
  color: #42b983;
}
</style> -->
