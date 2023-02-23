<script>
import MovieList from "../components/MovieList.vue";

export default {
  components: {
    MovieList,
  },
  methods: {
    eventhandler() {
      console.log("haiii");
    },
  },
};
</script>

<template>
  <MovieList></MovieList>
</template>
