<template>
  <v-container>
    <v-card
      class="mx-auto"
      max-width="1940"
    >
      <v-row>
        <v-col cols="12" md="1">
          <v-avatar size="80" class="icon">
            <img
            src="../images/persons/Yuuta Suzuki.png"
            alt="Yuuta Suzuki"
            >
          </v-avatar>
        </v-col>
        <v-col md="9">
          <v-card-title >Yuuta Suzuki</v-card-title>
        </v-col>
        <v-col md="2">
          <p>16/02/2020</p>
        </v-col>
      </v-row>
    </v-card>
  </v-container>
</template>

<script>
export default {
  props: ['tweetCarts']
}
</script>