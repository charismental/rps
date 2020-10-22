<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="text-h6 font-weight-medium">
        RockPaperScissors
        <!-- <v-icon>fa fa-lock</v-icon> -->
      </div>

      <v-spacer />

      <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <hello-world />
    </v-main>
  </v-app>
</template>

<script lang="ts">
  import Vue from 'vue'
  import HelloWorld from './components/HelloWorld.vue'

  export default Vue.extend({
    name: 'App',

    components: {
      HelloWorld,
    },

    data: () => ({
    //
    }),
  })
</script>
