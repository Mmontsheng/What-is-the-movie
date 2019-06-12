<template>
  <div>
    <div class="container">
      <div class="movie">
        <h1>Movie Summary</h1>
        <div class="row">
          <div class="col-md-4 col-sm-4 col-xs-12">
            <img :src="movie.Poster" class="img-fluid" :alt="movie.Title">
          </div>
          <div class="col-md-8 col-sm-8 col-xs-12">
            <h5>Title : {{ movie.Title }}</h5>
            <p>Language : {{ movie.Language }}</p>
            <p>Rated : {{ movie.Rated }}</p>
            <p>Year : {{ movie.Year }}</p>
            <p>Released : {{ movie.Released }}</p>
            <p>Actors : {{ movie.Actors }}</p>
            <p>Country : {{ movie.Country }}</p>
            <p>Genre : {{ movie.Genre }}</p>
            <p>IMDB Rating : {{ movie.imdbRating }}</p>
          </div>
        </div>
        <div class="row">
          <div class="summary">
            <div class="col-md-12">
              <h5>Summary</h5>
              <p>{{ movie.Plot }}</p>
              <router-link :to="{ name: 'home'}" class="btn">Go Back To Home</router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import apikey from "../../api.js";

export default {
  name: "movie",
  props: ["movieID"],
  data() {
    return {
      apikey: apikey,
      movie: []
    };
  },

  created() {
    axios
      .get(`https://www.omdbapi.com/?i=${this.movieID}&apikey=${this.apikey}`)
      .then(results => {
        let res = results.data;
        this.movie = res;
      });
  }
};
</script>

<style scoped>
.movie,
.summary {
  padding-top: 50px !important;
}

@media (max-width: 568px) {
  .movie,
  .summary {
    padding-top: 10px !important;
  }
}
</style>


