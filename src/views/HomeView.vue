<template>
  <Banner />
  <div class="main-container">
    <h1>Monte o Seu Burger</h1>
    <BurguerForm />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import Banner from "../components/Banner.vue";
import BurguerForm from "../components/BurguerForm.vue";

@Options({
  components: {
    Banner,
    BurguerForm,
  },
})
export default class HomeView extends Vue {}
</script>
