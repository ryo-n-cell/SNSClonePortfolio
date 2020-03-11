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
          src="../images/persons/1.jpeg"
          alt="Yuuta Suzuki"
          >
       </v-avatar>
      </v-img>
      <v-row>
        <v-col md="8" class="py-0">
          <v-card-title class="display-1">{{ userName }}</v-card-title>
        </v-col>
        <v-col md="4">
        <v-btn rounded color="primary" dark @click="profileBtn = !profileBtn">Profile Edit</v-btn>
        </v-col>
      </v-row>
      <v-card-subtitle class="py-0">@{{ loginId }}</v-card-subtitle>
      <v-card-text class="text--profile">
        <div>{{ profile }}</div>
        <div>
          <span class="numbersBold">10</span> Following / <span class="numbersBold">10</span> Followers &nbsp;
          <v-icon class="fas fa-map-marker-alt"></v-icon>
          {{ prefecture }},{{ country }}
        </div>
      </v-card-text>
    </v-card><br>
    <!-- プロフィールモーダル -->
    <v-dialog v-model="profileBtn" width="800px">
      <v-card>
        <v-card-title class="gray darken-2">Profile Edit</v-card-title>
        <v-container>
          <v-col cols="12">
            <v-text-field placeholder="name" />
          </v-col>
          <v-row justify="center" cols="10">
            <!-- <v-icon class="fas fa-map-marker-alt"></v-icon> -->
            <v-col col-5>
              <v-text-field placeholder="Prefecture" />
            </v-col>
            <v-col col-5>
              <v-text-field placeholder="Country" />
            </v-col>
            <v-col cols="12">
              <v-text-field placeholder="profile" />
            </v-col>
          </v-row>
          <v-card-actions>
          <v-spacer />
            <v-btn text color="primary" @click="profileBtn = false">Cancel</v-btn>
            <v-btn text @click="profileBtn = false">Edit</v-btn>
          </v-card-actions>
        </v-container>
      </v-card>
    </v-dialog>
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
      profileBtn: false,
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
  }
}
</script>