<template>
  <Navbar :alt="logo_alt" :logo="logo_src" />
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
  data() {
    return {
      logo_src: "logo.png",
      logo_alt: "logo ",
    };
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  font-family: "Helvetica";
}
</style>
