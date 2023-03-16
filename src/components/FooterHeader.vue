<template>
  <div class="footer">
    <p>f</p>
  </div>
</template>
<script lang="ts">
import { Options, Vue } from "vue-class-component";

@Options({
  props: {
    msg: String,
  },
})
export default class Footer extends Vue {
  msg!: string;
}
</script>
  <style scoped>
h3 {
  margin: 40px 0 0;
}
</style>
  