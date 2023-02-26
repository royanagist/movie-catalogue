<script>
import TrendingList from "../components/TrendingList.vue";
import UpcomingList from "../components/UpcomingList.vue";

export default {
  components: {
    TrendingList,
    UpcomingList,
  },
  methods: {
    eventhandler() {
      console.log("haiii");
    },
  },
};
</script>

<template>
  <TrendingList></TrendingList>
  <UpcomingList></UpcomingList>
</template>
