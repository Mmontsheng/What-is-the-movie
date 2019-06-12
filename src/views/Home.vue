<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-md-12">
          <div class="title text-center">
            <h1>What's the movie</h1>
          </div>
        </div>

        <div class="col-md-12">
          <search-movies v-on:searchMovie="search"/>
        </div>

        <div class="col-md-12" v-if="!movies">
          <h5 class="text-danger text-center">Movie not found</h5>
        </div>

        <div v-else class="col-md-12">
          <div class="row">
            <div class="col-md-3 col-sm-6 col-xs-12" v-for="(movie, index) in movies" :key="index">
              <movieSummary :movie="movie"/>
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
import searchMovies from "../components/SeachMovie.vue";
import movieSummary from "../components/MovieSummary.vue";
export default {
  name: "app",
  components: {
    searchMovies,
    movieSummary
  },
  data() {
    return {
      movies: [],
      apikey
    };
  },
  methods: {
    search(movie) {
      //console.log(movie);
      axios
        .get(`https://www.omdbapi.com/?s=${movie}&apikey=${this.apikey}`)
        .then(results => {
          let res = results.data;
          this.movies = res.Search;
        });
    }
  }
};
</script>

<style>
.title {
  padding-top: 50px;
}
p {
  color: #fff;
}
</style>
