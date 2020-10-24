<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="text-h6 font-weight-medium">
        Rock | Paper | Scissors
      </div>

      <v-spacer />
      <v-btn
        text
        @click="resetScores"
      >
        Start Over
      </v-btn>
    </v-app-bar>

    <v-main>
      <scoreboard
        :user-score="userScore"
        :comp-score="compScore"
      />
      <game @user-choice="updateUserChoice" />
      <v-dialog
        v-model="gameOver"
        persistent
        max-width="400"
      >
        <v-card height="300">
          <v-card-text class="pt-8">
            <div
              v-if="userChoice"
              class="text-h4 text-center"
            >
              You: <span class="success--text font-weight-bold">{{ userChoice }}</span>
            </div>
            <div
              v-if="compChoice"
              class="text-h4 text-center"
            >
              Com: <span class="success--text font-weight-bold">{{ compChoice }}</span>
            </div>
            <div
              class="text-h4 text-center"
            >
              {{ gameOverText }}
            </div>
          </v-card-text>
          <v-card-actions>
            <v-btn
              class="mx-auto"
              color="primary"
              @click="newGame"
            >
              Play New Game
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-main>
  </v-app>
</template>

<script lang="ts">
  import Vue from 'vue'
  import Scoreboard from './components/Scoreboard.vue'
  import Game from './components/Game.vue'

  export default Vue.extend({
    name: 'App',

    components: { Scoreboard, Game },

    data: (): {
      userChoice: string;
      compChoice: string;
      handOptions: string[];
      gameOver: boolean;
      gameOverText: string;
      userScore: number;
      compScore: number;
    } => ({
        userScore: 0,
        compScore: 0,
        userChoice: '',
        compChoice: '',
        gameOver: false,
        handOptions: [
          'rock',
          'paper',
          'scissors',
        ],
        gameOverText: '',
      }),
    methods: {
      resetScores (): void {
        this.userScore = 0
        this.compScore = 0
        this.newGame()
      },
      newGame (): void {
        this.userChoice = ''
        this.compChoice = ''
        this.gameOverText = ''
        this.gameOver = false
      },
      updateUserChoice (choice: string): void {
        this.userChoice = choice
        const index = Math.floor(Math.random() * 3)
        this.compChoice = this.handOptions[index]
        this.calculateWinner()
      },
      calculateWinner (): void {
        if (this.compChoice === this.userChoice) {
          this.gameOverText = 'Draw!'
        } else if ((this.compChoice === 'rock' && this.userChoice === 'paper') || (this.compChoice === 'paper' && this.userChoice === 'scissors') || (this.compChoice === 'scissors' && this.userChoice === 'rock')) {
          this.gameOverText = 'You Win!'
          this.userScore += 1
        } else {
          this.gameOverText = 'You Lose!'
          this.compScore += 1
        }
        this.gameOver = true
      },
    },
  })
</script>
