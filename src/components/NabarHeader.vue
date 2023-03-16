<template>
  <nav id="nav">
    <router-link to="/" id="lofoUrl">
      <img :alt="alt" :src="logo" id="logo" />
    </router-link>
    <router-link to="/">Home</router-link>
    <router-link to="/pedidos">About</router-link>
  </nav>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";

@Options({
  props: {
    msg: String,
    logo: String,
    alt: String,
  },
})
export default class HelloWorld extends Vue {
  msg!: string;
  logo!: string;
  alt!: string;
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#nav {
  background-color: #222;
  border-bottom: 4px solid #111;
  padding: 15px 50px;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}
#nav #lofoUrl {
  margin: auto;
  margin-left: 0;
}
#logo {
  height: 40px;
  width: 40px;
}
#nav a {
  text-decoration: none;
  color: #fcba03;
  margin: 12px;
  transition: 0.5s;
}
#nav a:hover {
  color: #fff;
}
</style>
