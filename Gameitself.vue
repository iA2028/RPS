<template>
  <div class="bg-color" ></div>

  <div class="bg-image" v-bind:style="{ backgroundImage: 'url(' + url + ')' }" v-if="result"></div>
  <div>
    <h2>Rock-Paper-Scissors</h2>
    <div>
      <label>Select the number of matches:</label>
      <input type="number" v-model="bestOf" min="3" max="5" />
    </div>
    <div>
      <button class="arcade-button" v-on:click="play('rock')">Rock</button>
      <button class="arcade-button" v-on:click="play('paper')">Paper</button>
      <button class="arcade-button" v-on:click="play('scissors')">Scissors</button>
    </div>
    <div v-if="result">
      <p>You chose: {{ playerChoice }}</p>
      <p>Computer chose: {{ computerChoice }}</p>
      <p>Result: {{ result }}</p>
      <p>Wins: {{ wins }}</p>
      <p>Losses: {{ losses }}</p>
</div>
<EndPage v-if="showEndPage" v-on:replay="resetGame"></EndPage>

  </div>
</template>






<script>
import EndPage from './EndPage.vue'

export default {
  components: {
    EndPage
  },

  data() {
    return {
      showEndPage: false,
      playerChoice: '',
      computerChoice: '',
      result: '',
      bestOf: 3,
      wins: 0,
      losses: 0,
      gifs: {
        rock: {
          win: 'src/assets/rock-paper-scissor.mp4',
          lose: 'src/assets/rock-loses.mov'
        },
        paper: {
          win: 'src/assets/rock-loses.mov',
          lose: 'src/assets/paper-loses.mov'
        },
        scissors: {
          win: 'src/assets/paper-loses.mov',
          lose: 'path/to/scissors-lose.gif'
        },
        tie: 'src/assets/RPSALL.mov'
      },
      url: ''
    }
  },
  methods: {
    play(choice) {
      this.playerChoice = choice
      this.computerChoice = this.getComputerChoice()
      this.result = this.getResult()
      if (this.result === 'You Win!') {
        this.wins += 1
        this.url = this.gifs[this.playerChoice].win
      } else if (this.result === 'You Lost!') {
        this.losses += 1
        this.url = this.gifs[this.playerChoice].lose
} else {
this.url = this.gifs.tie
}
if (this.wins >= this.bestOf || this.losses >= this.bestOf) {
this.endGame()
}
},
 resetGame() {
      this.playerChoice = ''
      this.computerChoice = ''
      this.result = ''
      this.wins = 0
      this.losses = 0
      this.url = ''
      this.showEndPage = false
    },
    endGame() {
      this.url = ''
      this.showEndPage = true
    },
getComputerChoice() {
const choices = ['rock', 'paper', 'scissors']
const randomIndex = Math.floor(Math.random() * 3)
return choices[randomIndex]
},
getResult() {
if (this.playerChoice === this.computerChoice) {
return 'Tie!'
} else if (
(this.playerChoice === 'rock' && this.computerChoice === 'scissors') ||
(this.playerChoice === 'paper' && this.computerChoice === 'rock') ||
(this.playerChoice === 'scissors' && this.computerChoice === 'paper')
) {
return 'You Win!'
} else {
return 'You Lost!'
}
}
}
}
</script>

<style scoped>

.bg-image{
 
  position: fixed;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  z-index: -1;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center center;
  background-color: #ffa800;
}

h2 {
  font-family: 'Pixelated', sans-serif;
  font-size: 7em;
  color: white;
  text-shadow: 3px 3px 3px #000;
  display: flex;
    justify-content: center;
    align-items: center;
    font-family: 'ArcadeClassic';
 
}

.arcade-button {
    background: linear-gradient(to bottom, #ffa800, #ff5e3a);
    padding: 115px 35px;
    border-radius: 8px;
    font-family: 'Pixelated', sans-serif;
    color: white;
    text-shadow: 2px 2px 2px #000;
    font-size: 1.2em;
box-shadow: 3px 3px 3px #000;

margin: 10px;
}
.arcade-button:hover {
background-color: darkgreen;
transform: scale(1.1);
}
.arcade-button:active {
transform: scale(0.9);
background-color: darkgreen;
}

@font-face {
  font-family: 'ArcadeClassic';
  src: url('src/assets/arcade_classic_2/ARCADECLASSIC.TTF') format('truetype');
}

.arcade-button {
  flex: 1;
}
</style>


