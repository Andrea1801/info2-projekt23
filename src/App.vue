<template>
  <v-app id="inspire">
    <!-- App bar na vrhu -->
    <v-app-bar app color="grey" >
      

      <v-spacer></v-spacer>

    

      <!-- Navigacijska traka -->
      <v-row>
        <v-btn
          v-for="link in links"
          :key="link.text"
          text
          :to="link.path"
        >
          {{ link.text }}
        </v-btn>
      </v-row>
    </v-app-bar>

    <!-- Glavni sadržaj -->
    <v-main>
      <router-view />
    </v-main>

    <!-- Bottom navigation -->
    <v-bottom-navigation app v-model="drawer" temporary color="browm" dark>
      <v-btn @click="toFacebook">
        <v-icon color="indigo darken-2">mdi-facebook</v-icon>
        Facebook
      </v-btn>

      <v-btn @click="toInstagram">
        <v-icon color="grey accent-3">mdi-instagram</v-icon>
        Instagram
      </v-btn>

      <v-btn @click="toYouTube">
        <v-icon color="red darken-1">mdi-youtube</v-icon>
        YouTube
      </v-btn>
    </v-bottom-navigation>
  </v-app>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    drawer: false,
    links: [
      {
        text: "Kokteli",
        path: "/",
      },
      {
        text: "Vaše mišljenje",
        path: "/komentar",
      },
      {
        text: "O nama",
        path: "/info",
      },
    ],
  }),
  methods: {
    toFacebook() {
      window.open("https://www.facebook.com/kokteli/?locale=nb_NO");
    },
    toInstagram() {
      window.open("https://www.instagram.com/kokteli.hr/");
    },
  
    toYouTube() {
      window.open("https://www.youtube.com/watch?v=b0IuTL3Z-kk&t=8s");
    },
  },
};
</script>

<style scoped>
main {
  background-image: url('assets/koktel.jpeg');
  background-position: center;
  background-attachment: fixed;
  background-repeat: no-repeat;
  background-size: cover;
}

</style>
