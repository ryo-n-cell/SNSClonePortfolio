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
          <v-card-title >{{ item.name }}</v-card-title>
        </v-col>
        <v-col md="2">
          <p>{{ item.tweet_at }}</p>
        </v-col>
      </v-row>
      <v-card-text class="headline font-weight-bold">
        {{ item.message }}
      </v-card-text>
      <!-- トグルで<color="blue lighten-2">追加 -->
      <v-btn class="ma-2" text icon>
        <v-icon @click="toggle_switch(item.tweet_ID)">mdi-thumb-up</v-icon>
        <!-- <v-icon v-show="item.likeBtn = true" @click="toggle_switch(item.tweet_ID)" color="blue lighten-2">mdi-thumb-up</v-icon> -->
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
    toggle_switch: function (id) {
      this.tweets[id].likeBtn = !this.tweets[id].likeBtn
      console.log(this.tweets[id].likeBtn)
    }
  },
  mounted () {
    axios.get('https://aqueous-scrubland-89182.herokuapp.com/user-statuses/' + this.id)
      .then(response => {
        console.log(response)
        let tweetsLength = response.data.tweets.length
        console.log(tweetsLength)
        for (let i = 0; i < tweetsLength; i++) {
          let tweetItem = {
            name: response.data.name,
            tweet_ID: response.data.tweets[i].id,
            message: response.data.tweets[i].tweet_message,
            tweet_at: response.data.tweets[i].created_at,
            likeBtn: false
          }
          console.log(tweetItem)
          this.tweets.push(tweetItem)
        }

        // let tweetsData = {
        //   name: response.data.name,
        //   tweetId: response.data.tweets.id,
        //   message: response.data.tweets.tweet_message,
        //   tweetDay: response.data.tweets.created_at,
        //   lakeBoolean: false
        // }
        // this.tweets.push(tweetsData)
        // console.log(this.tweets)
      }).catch(err => {
        console.log(err)
      })
  }
}
</script>