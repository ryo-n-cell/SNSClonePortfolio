<template>
  <v-container>
    <v-card
      class="mx-auto"
      max-width="1940"
      v-for="item in allTweets"
      :key="item.id"
    >
        <!-- v-for="item in tweets" -->
      <v-row>
        <v-col cols="auto" md="1">
          <v-avatar size="80" class="icon">
            <img
            v-bind:src="item.userIcon_URL"
            alt="userIcon"
            >
          </v-avatar>
        </v-col>
        <v-col md="9">
          <v-card-title class="display-1">{{ item.userName }}</v-card-title>
        </v-col>
        <v-col md="2">
          <p>{{ item.created_At }}</p>
        </v-col>
      </v-row>
      <v-card-text class="headline font-weight-bold">
        {{ item.tweetMessage }}
      </v-card-text>
      <!-- トグルで<color="blue lighten-2">追加 -->
      <v-btn class="ma-2" text icon>
        <v-icon>mdi-thumb-up</v-icon>
      </v-btn>
    </v-card>
  </v-container>
</template>

<script>
import axios from 'axios'
export default {
  props: ['timeLine'],
  data () {
    return {
      allTweets: [],
      userIcon_SRC: []
    }
  },
  methods: {
  },
  mounted () {
    axios.get('https://aqueous-scrubland-89182.herokuapp.com/all-tweets')
      .then(response => {
        console.log(response)
        let tweetsLength = response.data.length
        for (let i = 0; i < tweetsLength; i++) {
          let item = {
            tweet_ID: response.data[i].id,
            user_status_ID: response.data[i].user_status_id,
            // userIcon_URL: '../../images/persons/' + response.data[i].user_status_id + '.jpeg',
            userName: response.data[i].users_statuses[0].name,
            created_At: response.data[i].created_at,
            tweetMessage: response.data[i].tweet_message
          }
          this.allTweets.push(item)
          console.log(item)
        }
      }).catch(err => {
        console.log(err)
      })
  }
}
</script>
