<template>
  <v-container>
    <!-- プロフィール -->
    <v-card
      class="mx-auto"
      max-width="1940"
    >
      <v-img
        class="white--text align-end"
        height="200px"
        src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
      >
        <v-avatar size="150" class="icon">
          <img
          src="../images/persons/Yuuta Suzuki.png"
          alt="Yuuta Suzuki"
          >
       </v-avatar>
      </v-img>
      <v-row>
        <v-col md="8">
          <v-card-title >Yuuta Suzuki</v-card-title>
        </v-col>
        <v-col md="4">
          <v-btn
            color="orange"
            text
          >
            Edit profile
          </v-btn>
        </v-col>
      </v-row>
      <v-card-subtitle class="pb-0">@YutaSuzuki514</v-card-subtitle>

      <v-card-text class="text--profile">
        <div>Web&Software Developer HTML/CSS, Java Script, Vue.js＆Vutify,SQL,Linux
        </div>

        <div>
          <span class="numbersBold">10</span> Following / <span class="numbersBold">10</span> Followers &nbsp;
          <v-icon class="fas fa-map-marker-alt"></v-icon>
          Tokyo,Japan
        </div>
      </v-card-text>
    </v-card><br>
    <!-- ツイートゾーン -->
    <tweetCart v-bind="tweetCarts">
    </tweetCart>
  </v-container>
</template>

<style scoped>
span.numbersBold{
  font-weight: 800;
}
</style>

<script>
import tweetCart from '@/components/tweetCart'

export default {
  components: {
    tweetCart
  }
}
</script>