<template>
  <footer id="footer">
    <p>Make Your Burguer &copy; 2023</p>
  </footer>
</template>
<script lang="ts">
import { Options, Vue } from "vue-class-component";
@Options({
  props: {},
})
export default class Footer extends Vue {}
</script>

<style scoped>
#footer {
  height: 200px;
  background-color: #222;
  border-top: 4px solid #111;
  color: #fcba03;
  display: flex;
  justify-content: center;
  align-items: center;

  bottom: 0;
  width: 100%;
}
</style>
  