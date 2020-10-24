<template>
  <v-sheet
    elevation="0"
    class="mx-auto"
    max-width="600"
    height="150"
  >
    <v-row class="mt-6">
      <v-col
        cols="3"
        class="offset-md-2 offset-2 font-weight-bold"
        :class="$vuetify.breakpoint.smAndUp ? 'text-h2' : 'text-h4'"
      >
        You
      </v-col>
      <v-col
        cols="3"
      >
        <div
          class="font-weight-bold"
          :class="$vuetify.breakpoint.smAndUp ? 'text-h2' : 'text-h4'"
        >
          {{ userScore }} - {{ compScore }}
        </div>
      </v-col>
      <v-col
        class="font-weight-bold"
        :class="$vuetify.breakpoint.smAndUp ? 'text-h2' : 'text-h4'"
        cols="3"
      >
        Com
      </v-col>
    </v-row>
  </v-sheet>
</template>

<script lang="ts">
  import Vue from 'vue'

  export default Vue.extend({
    name: 'Scoreboard',
    props: {
      userScore: {
        type: Number,
      },
      compScore: {
        type: Number,
      },
    },
    data: () => ({}),
  })
</script>
