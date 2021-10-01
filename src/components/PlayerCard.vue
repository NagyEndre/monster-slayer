<template>
  <section>
    <h2>{{ name }} Health</h2>
    <img :src="avatarSrc" />
    <div class="healthbar">
      <div class="healthbar-value" :style="healthBarStyles"></div>
    </div>
  </section>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component'

@Options({
  props: {
    name: String,
    health: Number,
    avatarType: Number,
  },
})
export default class PlayerCard extends Vue {
  name = 'Player'
  health = 70
  avatarType = 2

  get avatarSrc() {
    return `https://robohash.org/${Math.random()}.png?set=set${this.avatarType}`
  }
  get healthBarStyles() {
    return { width: `${this.health}%` }
  }
}
</script>

<style scoped>
.healthbar {
  height: 40px;
  background: honeydew;
  border: 1px solid grey;
}
.healthbar-value {
  background-color: green;
  width: 100%;
  height: 100%;
}
h2 {
  margin-bottom: 0.25rem;
}
img {
  width: 25%;
}
</style>
