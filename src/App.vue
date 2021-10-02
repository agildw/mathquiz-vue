<template>
  <v-app>
    <v-app-bar app color="#F08A5D" dark>
      <div class="d-flex align-center">
        <v-icon x-large color="white">mdi-dome-light</v-icon>
        <span class="font-weight-bold">
          Apakah<span style="color: #e0f9b5">Vue</span></span
        >
      </div>

      <v-spacer></v-spacer>

      <!-- <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn> -->
    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    //
  }),
};
</script>
