<template>
  <header>
    <h1>Monster Slayer</h1>
  </header>
  <div>
    <PlayerCard name="Monster's" :health="monsterHealth" avatarType="2" class="container" />
    <PlayerCard name="Your" :health="playerHealth" avatarType="1" class="container" />
    <section v-if="winner" class="container">
      <h2>Game Over!</h2>
      <h3 v-if="winner === 'player'">You won!</h3>
      <h3 v-else-if="winner === 'monster'">Monster won!</h3>
      <h3 v-else-if="winner === 'draw'">It's a draw!</h3>
    </section>
    <section id="controlls" class="container">
      <button @click="attackMonster">ATTACK</button>
      <button @click="specialAttack" :disabled="attackNotAvailable">SPECIAL ATTACK</button>
      <button @click="healPlayer" :disabled="canNotHeal">HEAL</button>
      <button>SURRENDER</button>
    </section>
    <section class="container">
      <h2>Battle log</h2>
      <ul></ul>
    </section>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component'
import PlayerCard from './components/PlayerCard.vue'

@Options({
  components: { PlayerCard },
  watch: {
    playerHealth(value){
      if(value === 0) {
        if(this.monsterHealth === 0){
          this.winner = 'draw'
        } else {
          this.winner = 'monster'
        }
      }
    },
    monsterHealth(value){
      if(value === 0){
        if(this.playerHealth === 0){
          this.winner = 'draw'
        } else {
          this.winner = 'player'
        }
      }
    }
  }
})
export default class App extends Vue {
  private readonly MAX_HEALTH = 100

  monsterHealth = this.MAX_HEALTH
  playerHealth = this.MAX_HEALTH

  private roundCount = 0
  private isAttackUsed = false

  winner = null

  get attackNotAvailable() {
    if (this.roundCount % 3 === 0) {
      this.isAttackUsed = false
    }
    return this.isAttackUsed
  }

  get canNotHeal() {
    return this.playerHealth === this.MAX_HEALTH
  }

  attackMonster(): void {
    this.roundCount++
    const attackValue = this.getRandomNumber(5, 10)
    const calculatedHealth = (this.monsterHealth -= attackValue)
    this.monsterHealth = calculatedHealth < 0 ? 0 : calculatedHealth
    this.attackPlayer()
  }

  attackPlayer(): void {
    const attackValue = this.getRandomNumber(2, 12)
    const calculatedHealth = (this.playerHealth -= attackValue)
    this.playerHealth = calculatedHealth < 0 ? 0 : calculatedHealth
  }

  specialAttack() {
    this.roundCount++
    const attackValue = this.getRandomNumber(10, 20)
    this.monsterHealth -= attackValue
    this.isAttackUsed = true
    this.attackPlayer()
  }

  healPlayer() {
    this.roundCount++
    const healValue: number = this.getRandomNumber(5, 15)
    const calculatedHealth: number = (this.playerHealth += healValue)

    this.playerHealth = calculatedHealth > this.MAX_HEALTH ? this.MAX_HEALTH : calculatedHealth

    this.attackPlayer()
  }
  private getRandomNumber(min: number, max: number): number {
    return Math.floor(Math.random() * (max - min)) + min
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}
html {
  font-family: 'Jost', sans-serif;
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
button:hover {
  background-color: #cc0010;
  transform: scale(1.1);
}
.container {
  widows: 90%;
  max-width: 40rem;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 14px;
  padding: 0.5rem;
  text-align: center;
}
#controlls {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
}
button:disabled {
  background: grey;
  transform: none;
  cursor: not-allowed;
}
</style>
