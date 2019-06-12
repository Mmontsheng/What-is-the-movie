<template>
  <div>
      <div class="text-center movie" @click="viewMovie(movie.imdbID)">
        <img
          v-if="movie.Poster=='N/A'"
          :alt="movie.Title"
          class="img-fluid"
          src="../assets/fallback.jpg"
        >
        <img v-else :src="movie.Poster" :alt="movie.Title" class="img-fluid">
        <p class="movie-title">{{ movie.Title }}</p>
      </div>
  </div>
</template>

<script>
export default {
  name: "movieSummary",
  props: {
    movie: Object
  },
  methods: {
    viewMovie(id) {
       this.$router.push({
        name: "movie",
        params: { movieID: id }
      });
     // console.log(id);
    }
  }
};
</script>

<style scoped>
h4 {
  color: #fff;
}

img {
  height: 300px !important;
}

.movie {
  margin: 10px;
  padding: 0;
  position: relative;
  cursor: pointer;
}
p.movie-title {
  position: relative;
  bottom: 45px;
  z-index: 1;
  color: #fff;
  padding: 0 !important;
  margin: 0 !important;
}
a {
  margin: 0 !important;
  position: relative;
  top: 0;
}
</style>
