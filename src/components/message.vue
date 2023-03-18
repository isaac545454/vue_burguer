<template>
  <div class="message-container">
    <p>{{ msg }}</p>
  </div>
</template>

<script>
import { Vue, Options } from "vue-class-component";

@Options({
  props: {
    msg: String,
  },
})
export default class Message extends Vue {}
</script>

<style scoped>
.message-container {
  color: #004085;
  background: #cce5ff;
  border: 2px solid #88daff;
  border-radius: 5px;
  padding: 10px;
  width: 400px;
  margin: 10px auto;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>