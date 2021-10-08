<template>
  <h2>{{ name }} Health</h2>
  <img :src="avatarSrc" />
  <div class="healthbar">
    <div class="healthbar-value" :style="healthBarStyles"></div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component'

@Options({
  props: {
    name: String,
    health: {
      type: Number,
      default: 100,
    },
    avatarType: {
      type: Number,
      default: 2,
    },
  },
})
export default class PlayerCard extends Vue {
  name!: string
  health!: number
  avatarType!: number

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
