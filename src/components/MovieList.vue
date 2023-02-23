<script>
import axios from "axios";
import MovieItem from "./MovieItem.vue";
import ToggleTrending from "./ToggleTrending.vue";

export default {
  components: {
    ToggleTrending,
    MovieItem,
  },
  data() {
    return {
      baseUrl: "https://api.themoviedb.org/3",
      apiKey: "34d34267d847a654c9ca7590fffc4fbb",
      trendingPeriod: "day",
      trendingList: [],
    };
  },
  methods: {
    async fetchTrending() {
      try {
        const { data } = await axios({
          url: `${this.baseUrl}/trending/movie/${this.trendingPeriod}?api_key=${this.apiKey}`,
          method: "get",
        });
        this.trendingList = data.results;
        console.log(this.trendingList[0]);
      } catch (error) {
        console.log(error);
      }
    },
    switchTrending() {
      if (this.trendingPeriod === "day") {
        this.trendingPeriod = "week";
      } else {
        this.trendingPeriod = "day";
      }
      this.fetchTrending();
    },
  },
  created() {
    this.fetchTrending();
  },
};
</script>

<template>
  <div class="d-flex align-items-center mb-4">
    <h1>Trending</h1>
    <ToggleTrending @switchTrending="switchTrending"></ToggleTrending>
  </div>
  <div class="row justify-content-center">
    <MovieItem
      v-for="item in trendingList"
      :key="item.id"
      :title="item.title"
      :poster_path="item.poster_path"
      :release_date="item.release_date"
    ></MovieItem>
  </div>
</template>
