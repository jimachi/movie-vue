<template>
  <div id="app">
    <Header></Header>
    <br><br>
    <input type="text" v-model="searchText">
    <button @click="searchMovies">検索</button>
    <br>
    <ul v-if="movies">
      <li v-for="movie in movies.Search" :key="movie">
        {{ movie.Title }}
        <img width="200" :src=movie.Poster>
      </li>

    </ul>
    
    <!-- <img width="200" :src=showPoster alt=""> -->
  </div>
</template>

<script>
import axios from "axios"
import Header from "./components/Header"

export default {
  name: 'app',
  data () {
    return {
      movies: [],
      searchText: ""
    }
  },
  components: {
    Header
  },
  computed: {
    showPoster: function() {
      console.log("pos", this.info.Poster)
      return this.info.Poster;
    }
  },
  methods: {
    searchMovies: function(){
      axios
        .get(`http://www.omdbapi.com/?apikey=33d8c9d8&s=${this.searchText}`)
        .then(response => {
          this.movies = response.data
          console.log("movies", this.movies)
        })
    }
  }
}
</script>

<style lang="scss">
</style>
