<template>
  <header>Monster Slayer</header>
  <div>
    <section>
      <h2>Monster Health</h2>
      <div>
        <div></div>
      </div>
    </section>
    <section>
      <h2>Your Health</h2>
      <div>
        <div></div>
      </div>
    </section>
    <section>
      <button>ATTACK</button>
      <button>SPECIAL ATTACK</button>
      <button>HEAL</button>
      <button>SURRENDER</button>
    </section>
    <section>
      <h2>Battle log</h2>
      <ul></ul>
    </section>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import HelloWorld from "./components/HelloWorld.vue";

@Options({
  components: {
    HelloWorld,
  },
})
export default class App extends Vue {}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
