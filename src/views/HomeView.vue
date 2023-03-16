<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <NabarHeader msg="Welcome to Your Vue.js + TypeScript App" />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import NabarHeader from "@/components/NabarHeader.vue"; // @ is an alias to /src

@Options({
  components: {
    NabarHeader,
  },
})
export default class HomeView extends Vue {}
</script>
