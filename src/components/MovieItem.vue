<script>
export default {
  data() {
    return {
      imgUrl: "",
      color: "red",
    };
  },
  props: {
    title: String,
    release_date: String,
    poster_path: String,
  },
  created() {
    const Url = `https://image.tmdb.org/t/p/w500${this.poster_path}`;
    this.imgUrl = Url;
  },
  computed: {
    style() {
      return `--bg-var: url(${this.imgUrl})`;
    },
  },
};
</script>

<template>
  <div class="flex-grow-0 d-flex flex-column col">
    <div class="card" :style="style"></div>
    <div class="movie-info">
      <p class="fw-bold mb-0">{{ title }}</p>
      <p class="text-secondary">{{ release_date }}</p>
    </div>
  </div>
</template>

<style scoped>
.movie-info {
  margin: 0 10px;
}
.card {
  width: 150px;
  height: 220px;
  background: #07182e;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  place-content: center;
  place-items: center;
  overflow: hidden;
  border-radius: 20px;
  margin: 10px;
}

.card h2 {
  z-index: 1;
  color: white;
  font-size: 2em;
}

.card::before {
  content: "";
  position: absolute;
  width: 100px;
  background-image: -webkit-gradient(
    linear,
    left top,
    left bottom,
    from(rgb(0, 183, 255)),
    to(rgb(255, 48, 255))
  );
  background-image: linear-gradient(
    180deg,
    rgb(0, 183, 255),
    rgb(255, 48, 255)
  );
  height: 130%;
  -webkit-animation: rotBGimg 3s linear infinite;
  animation: rotBGimg 3s linear infinite;
  -webkit-transition: all 0.2s linear;
  transition: all 0.2s linear;
}

@-webkit-keyframes rotBGimg {
  from {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }

  to {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}

@keyframes rotBGimg {
  from {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }

  to {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}

.card::after {
  content: "";
  position: absolute;
  background: var(--bg-var) center center;
  background-size: cover;
  inset: 5px;
  border-radius: 15px;
}
/* .card:hover:before {
  background-image: linear-gradient(180deg, rgb(81, 255, 0), purple);
  animation: rotBGimg 3.5s linear infinite;
} */
</style>
