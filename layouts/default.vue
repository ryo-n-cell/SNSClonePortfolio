<template>
  <v-app id="inspire">
    <!-- サイドバー -->
    <v-navigation-drawer v-model="drawer" :clipped="$vuetify.breakpoint.lgAndUp" app>
      <v-list dense>
        <v-list-item-group color="primary">
          <v-list-item
            v-for="(item, i) in items"
            :key="i"
            :inactive="inactive"
            @click.native="transitionPages(i)"
          >
            <v-list-item-icon>
              <v-icon v-text="item.icon"></v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title v-text="item.text"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <!-- ヘッダー -->
    <v-app-bar :clipped-left="$vuetify.breakpoint.lgAndUp" app color="blue darken-3" dark>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title style="width: 300px" class="ml-0 pl-4">
        <span class="hidden-sm-and-down">SNS Clone Portfolio</span>
      </v-toolbar-title>
      <v-spacer />
      <span>Ryota Nakamura</span>
      <v-btn href="https://github.com/ryo-n-cell/SNSClonePortfolio" target="_blank" icon>
        <v-icon>fab fa-github</v-icon>
      </v-btn>
      <v-btn href="https://twitter.com/BYEt0Vysprss9Ev" target="_blank" icon>
        <v-icon>fab fa-twitter</v-icon>
      </v-btn>
      <v-btn href="https://note.com/ryonjs" target="_blank" icon>
        <v-icon>far fa-sticky-note</v-icon>
      </v-btn>
      <v-btn href="https://vuetifyjs.com/ja/" target="_blank" icon large>
        <v-avatar size="32px" item>
          <v-img src="https://cdn.vuetifyjs.com/images/logos/logo.svg" alt="Vuetify" />
        </v-avatar>
      </v-btn>
    </v-app-bar>

    <v-content>
      <nuxt />
    </v-content>

    <!-- 右下モーダルボタン -->
    <v-btn bottom color="pink" dark fab fixed right @click="dialog = !dialog">
      <v-icon>fas fa-microphone</v-icon>
    </v-btn>
    <!-- モーダルトグル -->
    <v-dialog v-model="dialog" width="800px">
      <v-card>
        <v-card-title class="grey darken-2">Create tweet！</v-card-title>
        <v-container>
          <v-row class="mx-2">
            <v-col class="align-center justify-space-between" cols="12">
              <v-row align="center" class="mr-0">
                <v-avatar size="40px" class="mx-3">
                  <img 
                  src="../images/persons/Yuuta Suzuki.png" 
                  alt = "Yuuta Suzuki" >
                </v-avatar>
                <v-text-field placeholder="Yuta Suzuki" />
              </v-row>
            </v-col>
            <v-col cols="12">
              <v-text-field prepend-icon="far fa-comment" placeholder="Tweet" />
            </v-col>
          </v-row>
        </v-container>
        <v-card-actions>
          <v-spacer />
          <v-btn text color="primary" @click="dialog = false">Cancel</v-btn>
          <v-btn text @click="dialog = false">Tweet</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-app>
</template>

<script>
export default {
  props: {
    source: String
  },
  data: () => ({
    dialog: false,
    drawer: null,
    // selecting: 0,
    items: [
      { icon: 'mdi-account', url: '/', text: 'プロフィール' },
      { icon: 'mdi-account-multiple', url: '/timeline', text: 'タイムライン' },
      { icon: 'mdi-email-outline', url: '/directMail', text: 'ダイレクトメール' },
      { icon: 'mdi-bell-ring-outline', url: '/notifications', text: '通知' },
      { icon: 'mdi-card-text-outline', url: '/news', text: 'ニュース' },
      { icon: 'mdi-calendar-month', url: '/calender', text: 'カレンダー' },
      { icon: 'mdi-cloud-outline', url: '/weather', text: '天気' },
      { icon: 'mdi-help-circle', url: '/help', text: 'ヘルプ' }
    ]
  }),
  methods: {
    transitionPages: function (pageId) {
      console.log(pageId)
      if (pageId === 0) {
        this.$router.push('/')
      } else if (pageId === 1) {
        this.$router.push('/timeline')
      } else if (pageId === 2) {
        this.$router.push('/directMail')
      } else if (pageId === 3) {
        this.$router.push('/notifications')
      } else if (pageId === 4) {
        this.$router.push('/news')
      } else if (pageId === 5) {
        this.$router.push('/calendar')
      } else if (pageId === 6) {
        this.$router.push('/weather')
      } else if (pageId === 7) {
        this.$router.push('/help')
      }
    }
  }
}
</script>