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
          <v-card-title >{{ userName }}</v-card-title>
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
      <v-card-subtitle class="pb-0">@{{ loginId }}</v-card-subtitle>
      <v-card-text class="text--profile">
        <div>{{ profile }}</div>
        <div>
          <span class="numbersBold">10</span> Following / <span class="numbersBold">10</span> Followers &nbsp;
          <v-icon class="fas fa-map-marker-alt"></v-icon>
          {{ prefecture }},{{ country }}
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
// import axios from 'axios'

export default {
  components: {
    tweetCart
  },
  data () {
    return {
      id: 1,
      userName: null,
      profile: null,
      loginId: null,
      prefecture: null,
      country: null,
      icon: null
    }
  },
  mounted () {
    // 決められたAPIを取得するため一時的に定数にしている
    // data内のidを+してfetchでAjax通信してAPIを取得
    const url = 'https://aqueous-scrubland-89182.herokuapp.com/user-statuses/'
    fetch(url + this.id)
      .then(Response => {
        Response.json().then(userData => {
          console.log(userData)
          this.userName = userData.name
          this.loginId = userData.login_id
          this.profile = userData.profile
          // this.following = userData.****
          // this.followers = userData.****
          this.prefecture = userData.prefecture
          this.country = userData.country
          this.icon = userData.icon
        }).catch(err => {
          console.error(err)
        })
      })
    // const iconUrl = 'https://aqueous-scrubland-89182.herokuapp.com/uploads/7290573031ff40b08c66a3ad84d3371e.png'
    // fetch(iconUrl)
    //   .then(Response => {
    //     Response.json().then(iconData => {
    //       console.log(iconData)
    //     })
    //   })
  }
}
</script>