<template>
  <section>
    <slot></slot>
  </section>
</template>
<script lang="ts">
import { Options, Vue } from 'vue-class-component'
export default class App extends Vue {}
</script>
<style scoped>
section {
  widows: 90%;
  max-width: 40rem;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 14px;
  padding: 0.5rem;
  text-align: center;
}
</style>
