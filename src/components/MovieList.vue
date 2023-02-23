<script>
import axios from "axios";
import { Swiper, SwiperSlide } from "swiper/vue";
import { EffectCoverflow, Pagination } from "swiper";
import MovieItem from "./MovieItem.vue";
import ToggleTrending from "./ToggleTrending.vue";

export default {
  components: {
    ToggleTrending,
    MovieItem,
    Swiper,
    SwiperSlide,
  },
  setup() {
    return {
      modules: [EffectCoverflow, Pagination],
    };
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
  mounted() {
    // const swiperSlide = document.querySelectorAll(".swiper-slide");
    const swiperSlide = document.getElementsByClassName("swiper-slide");
    console.log(swiperSlide);
  },
};
</script>

<template>
  <div class="d-flex align-items-center">
    <h1>Trending</h1>
    <ToggleTrending @switchTrending="switchTrending"></ToggleTrending>
  </div>
  <swiper
    :effect="'coverflow'"
    :grabCursor="true"
    :centeredSlides="true"
    :slidesPerView="'auto'"
    :coverflowEffect="{
      rotate: -10,
      stretch: 0,
      depth: 300,
      modifier: 0.3,
      slideShadows: false,
    }"
    :spaceBetween="10"
    :pagination="{
      clickable: true,
    }"
    :loop="true"
    :breakpoints="{
      '640': {
        slidesPerView: 2,
        spaceBetween: 20,
      },
      '768': {
        slidesPerView: 4,
        spaceBetween: 40,
      },
      '1024': {
        slidesPerView: 7,
        spaceBetween: 50,
      },
    }"
    :modules="modules"
  >
    <swiper-slide v-for="item in trendingList" :key="item.id">
      <MovieItem
        :title="item.title"
        :poster_path="item.poster_path"
        :release_date="item.release_date"
      ></MovieItem>
    </swiper-slide>
  </swiper>
</template>
