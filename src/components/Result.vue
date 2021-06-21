<template>
  <v-container>
    <div class="Result">
      <h1>This is an Result page: {{ data }}</h1>
    </div>
    <v-row class="text-center">
      <!-- <v-col cols="12"> </v-col> -->

      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          検索結果
        </h1>
        <p>検索キーワード：{{ $route.params.keyword }}</p>
        <!-- router.jsで設定した~/:hogeを取得できる -->

        <!-- <p>現在のパス：{{ $route.path }}</p> -->
        <!-- <p>現在のquery：{{ $route.query }}</p> // 今はないので何も表示されない-->
        <!-- <p>現在のhash：{{ $route.hash }}</p> // 今はないので何も表示されない-->
        <v-flex mb-5 xs12>
          <v-card
            v-for="album in albums"
            class="mx-auto"
            max-width="344"
            color="black"
            dark
            :key="album.key"
            style="margin-bottom: 10px;"
            :href="album.collectionViewUrl"
            target="_blank"
            rel="noopener"
          >
            <v-img :src="album.artworkUrl100"></v-img>

            <v-card-title v-text="album.collectionName"> </v-card-title>

            <v-card-subtitle v-text="album.artistName"> </v-card-subtitle>
          </v-card>
        </v-flex>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      albums: [],
    };
  },
  created() {
    const vm = this;
    axios
      .get(
        `https://itunes.apple.com/search?term=${this.$route.params.keyword}&entity=album`
      )
      .then((response) => {
        console.log(response);
        vm.albums = response.data.results;
      });
  },
};
</script>
