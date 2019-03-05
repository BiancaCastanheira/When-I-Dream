<template>
  <v-container fluid style="min-height: 0;" grid-list-md>
    <v-layout row wrap>
      <v-flex md4>
        <v-card height="500" color="deep-purple darken-4" dark>
          <v-card-title>Nightmare</v-card-title>
        </v-card>
      </v-flex>
      <v-flex md4>
        <v-layout column class="text-xs-center">
          <v-layout row justify-center align-center>
            <v-btn color="deep-purple darken-4" fab class="mr-4"></v-btn>
            <v-btn color="yellow lighten-4" fab class="ml-4"></v-btn>
          </v-layout>

          <v-card height="400">
            
          </v-card>
          <v-progress-linear
            color="error"
            height="20"
            value="75"
          ></v-progress-linear>
        </v-layout>
      </v-flex>
      <v-flex md4>
        <v-card height="500" color="yellow lighten-4">
          <v-card-title>Dreams</v-card-title>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
}
</script>
