<template>
  <v-app>
    <v-app-bar app color="pink" dark>
      <div class="d-flex align-center">
        <router-link to="/" style="color: white; text-decoration: none;">
          <h1>SEARCH MUSIC</h1>
        </router-link>
      </div>

      <v-spacer></v-spacer>

      <v-btn to="/" color="red">
        <span class="mr-2">HOME</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
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
