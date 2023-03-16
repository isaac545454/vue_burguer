<template>
  <div class="home"></div>
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
