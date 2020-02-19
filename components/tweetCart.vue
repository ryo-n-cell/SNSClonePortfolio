<template>
  <v-container>
    <v-card
      class="mx-auto"
      max-width="1940"
    >
      <v-row>
        <v-col cols="auto" md="1">
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
          <p>Feb 11</p>
        </v-col>
      </v-row>
      <v-card-text class="headline font-weight-bold">
        "Turns out semicolon-less style is easier and safer in TS because most gotcha edge cases are type invalid as well."
      </v-card-text>
      <!-- トグルで<color="blue lighten-2">追加 -->
      <v-btn class="ma-2" text icon>
        <v-icon>mdi-thumb-up</v-icon>
      </v-btn>
    </v-card>
  </v-container>
</template>

<script>
export default {
  props: ['tweetCarts'],
  data () {
    return {
      tweet: [
        { id: '0',
          message: 'Turns out semicolon-less style is easier and safer in TS because most gotcha edge cases are type invalid as well'
        },
        { id: '1',
          message: 'I love Vue.'
        },
        { id: '2',
          message: '日本語久々にしゃべったわ.'
        },
        { id: '3',
          message: 'I spend as much time studying as I do sleeping. '
        },
        { id: '4',
          message: 'YesYesYesYesYesYesYesYesYesYesYesYesYesYesYesYesYesYesHooooooooooooooooooooooooooooo.'
        }
      ]
    }
  }
}
</script>