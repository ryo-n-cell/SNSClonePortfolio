<template>
  <v-container>
    <v-card
      class="mx-auto"
      max-width="1940"
      v-for="item in tweets"
      :key="item.id"
    >
        <!-- v-for="item in tweets" -->
      <v-row>
        <v-col cols="auto" md="1">
          <v-avatar size="80" class="icon">
            <img
            src="../images/persons/1.jpeg"
            alt="userIcon"
            >
          </v-avatar>
        </v-col>
        <v-col md="9">
          <v-card-title >Yuuta Suzuki</v-card-title>
        </v-col>
        <v-col md="2">
          <p>Feb 11</p>
        </v-col>
      </v-row>
      <v-card-text class="headline font-weight-bold">
        {{ item.tweet_message }}
      </v-card-text>
      <!-- トグルで<color="blue lighten-2">追加 -->
      <v-btn @click="take_API" class="ma-2" text icon>
        <v-icon>mdi-thumb-up</v-icon>
      </v-btn>
    </v-card>
  </v-container>
</template>

<script>
import axios from 'axios'
export default {
  props: ['tweetCarts'],
  data () {
    return {
      id: 1,
      tweets: [],
      icon: ''
    }
  },
  methods: {
  },
  mounted () {
    axios.get('https://aqueous-scrubland-89182.herokuapp.com/user-statuses/' + this.id)
      .then(response => {
        console.log(this.tweets)
        // console.log(response.data.icon.url)
        this.tweets = response.data.tweets
        // this.icon = 'https://aqueous-scrubland-89182.herokuapp.com/' + response.data.icon.url
        // console.log(this.icon)
      }).catch(err => {
        console.log(err)
      })
  }
}
</script>