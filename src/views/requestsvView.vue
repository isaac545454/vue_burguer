<template>
  <div class="main-container">
    <h1>Gerenciar Pedidos:</h1>
    <Deshboard />
  </div>
</template>


<script lang="ts">
import { Vue, Options } from "vue-class-component";
import Deshboard from "../components/Dashboard.vue";

@Options({
  components: {
    Deshboard,
  },
})
export default class RequestView extends Vue {}
</script>