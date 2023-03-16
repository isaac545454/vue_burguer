<template>
  <Banner />
  <div class="main-container">
    <h1>Monte o Seu Burger</h1>
    <p>Form</p>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import Banner from "../components/Banner.vue";

@Options({
  components: {
    Banner,
  },
})
export default class HomeView extends Vue {}
</script>
