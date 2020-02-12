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
          >
             <!-- <nuxt-link to= "/help" > -->
              <v-list-item-icon>
                <v-icon v-text="item.icon"></v-icon>
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title v-text="item.text"></v-list-item-title>
              </v-list-item-content>
             <!-- </nuxt-link> -->
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
      <v-btn icon>
        <v-icon>fab fa-github</v-icon>
      </v-btn>
      <v-btn icon>
        <v-icon>fab fa-twitter</v-icon>
      </v-btn>
      <v-btn icon>
        <v-icon>far fa-sticky-note</v-icon>
      </v-btn>
      <v-btn icon large>
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
      <v-icon>mdi-plus</v-icon>
    </v-btn>
    <!-- モーダルトグル -->
    <v-dialog v-model="dialog" width="800px">
      <v-card>
        <v-card-title class="grey darken-2">Create contact</v-card-title>
        <v-container>
          <v-row class="mx-2">
            <v-col class="align-center justify-space-between" cols="12">
              <v-row align="center" class="mr-0">
                <v-avatar size="40px" class="mx-3">
                  <img src="//ssl.gstatic.com/s2/oz/images/sge/grey_silhouette.png" alt />
                </v-avatar>
                <v-text-field placeholder="Name" />
              </v-row>
            </v-col>
            <v-col cols="6">
              <v-text-field prepend-icon="mdi-account-card-details-outline" placeholder="Company" />
            </v-col>
            <v-col cols="6">
              <v-text-field placeholder="Job title" />
            </v-col>
            <v-col cols="12">
              <v-text-field prepend-icon="mdi-mail" placeholder="Email" />
            </v-col>
            <v-col cols="12">
              <v-text-field type="tel" prepend-icon="mdi-phone" placeholder="(000) 000 - 0000" />
            </v-col>
            <v-col cols="12">
              <v-text-field prepend-icon="mdi-text" placeholder="Notes" />
            </v-col>
          </v-row>
        </v-container>
        <v-card-actions>
          <v-btn text color="primary">More</v-btn>
          <v-spacer />
          <v-btn text color="primary" @click="dialog = false">Cancel</v-btn>
          <v-btn text @click="dialog = false">Save</v-btn>
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
    transitionPage: function (pageId) {
      console.log(pageId)
      if (pageId === 0) {
        location.href = '/'
      } else if (pageId === 1) {
        location.href = '/timeline'
      } else if (pageId === 2) {
        location.href = 'directMail'
      } else if (pageId === 3) {
        this.$route.push({ path: 'notifications' })
        // location.href = '/notifications'
      } else if (pageId === 4) {
        location.href = '/news'
      } else if (pageId === 5) {
        location.href = '/calendar'
      } else if (pageId === 6) {
        location.href = 'weather'
      } else if (pageId === 7) {
        location.href = '/help'
      }
    }
  }
}
</script>