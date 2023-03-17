<template>
  <div id="main-banner">
    <h1>Make Your Burger</h1>
  </div>
</template>

<script>
import { Options, Vue } from "vue-class-component";
@Options({
  props: {},
})
export default class Banner extends Vue {}
</script>
<style scoped>
#main-banner {
  background-image: url("../../public/burger.jpg");
  background-position: 0 -250px;
  background-size: cover;
  height: 500px;
  display: flex;
  align-items: center;
  justify-content: flex-start;
}
#main-banner h1 {
  color: #fff;
  text-align: center;
  font-size: 60px;
  background: #222;
  padding: 20px 40px;
}
</style>