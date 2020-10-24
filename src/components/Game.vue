<template>
  <v-card
    elevation="0"
    max-width="600"
    height="200"
    class="d-flex justify-space-around mx-auto align-center"
  >
    <v-btn
      fab
      :height="96"
      :width="96"
      elevation="0"
      @click="shoot('rock')"
    >
      <v-icon size="72">
        fa fa-hand-rock-o
      </v-icon>
    </v-btn>
    <v-btn
      fab
      :height="96"
      :width="96"
      elevation="0"
      @click="shoot('paper')"
    >
      <v-icon size="72">
        fa fa-hand-paper-o
      </v-icon>
    </v-btn>
    <v-btn
      fab
      :height="96"
      :width="96"
      elevation="0"
      @click="shoot('scissors')"
    >
      <v-icon size="72">
        fa fa-hand-scissors-o
      </v-icon>
    </v-btn>
  </v-card>
</template>

<script lang="ts">
  import Vue from 'vue'

  export default Vue.extend({
    name: 'Game',
    data: (): {
      userChoice: string;
    } => ({
        userChoice: '',
      }),
    methods: {
      shoot (choice: string): void {
        this.userChoice = choice
        this.$emit('user-choice', choice)
      },
    },
  })
</script>
