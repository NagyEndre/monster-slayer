<template>
  <header>
    <h1>Monster Slayer</h1>
  </header>
  <div>
    <section>
      <h2>Monster Health</h2>
      <div class="healthbar">
        <div class="healthbar-value"></div>
      </div>
    </section>
    <section>
      <h2>Your Health</h2>
      <div class="healthbar">
        <div class="healthbar-value"></div>
      </div>
    </section>
    <section id="controlls">
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

@Options({
  components: {
  },
})
export default class App extends Vue {}
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: "Jost", sans-serif;
}

body {
  margin: 0;
}

header {
  background-color: #880017;
  color: white;
  text-align: center;
  box-shadow: 0 10px 10px rgba(0, 0, 0, 0.26);
  padding: 0.5rem;
  margin-bottom: 2rem;
}
section {
  widows: 90%;
  max-width: 40rem;

  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 14px;
  padding: 0.5rem;
  text-align: center;
}
button {
  font: inherit;
  background-color: #880017;
  color: white;
  padding: 1rem 2rem;
  border-radius: 1rem;
  margin: 1rem;
  cursor: pointer;
  width: 14rem;
}

.healthbar {
  width: 100%;
  height: 40px;
  background: honeydew;
  border: 1px solid grey
}
.healthbar-value{
  background-color: green;
  width: 80%;
  height: 100%;
}
#controlls{
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
}
</style>
