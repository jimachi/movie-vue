<template>
  <div id="app">
    <Header></Header>
    <br><br>
    <input type="text" v-model="searchText">
    <button @click="searchMovies">検索</button>
    <br>
    <!-- <ul v-if="movies">
      <li v-for="movie in movies.Search" :key="movie">
        {{ movie.Title }}
        {{ movie.Year }}
        {{ movie.Type }}
        <img width="200" :src=movie.Poster>
      </li>
    </ul> -->
    <div v-for="movie in movies.Search" class="card" :key="movie">
      <img :src=movie.Poster :alt=movie.Title class="image">
      <p class="title">{{ movie.Title }}</p>
      <p class="content">Year: {{ movie.Year }}</p>
    </div>
    
    <!-- <img width="200" :src=showPoster alt=""> -->
  </div>
</template>

<script>
import "normalize.css";
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

<style>
body {
  background-color: #ededed;
}
img, p {
  margin: 0;
  padding: 0;
}
p {
  font-size: 100%;
  line-height: 1;
}
#app {
  width: 100%;
}
.card {
  display: inline-block;
  width: 250px;
  margin: 20px;
  border-radius: 5px;
  background-color: #fff;
  box-shadow: 0 3px 6px #ccc;
}
.image {
  width: 250px;
  height: 100%;
  object-fit: cover;
  border-radius: 5px 5px 0 0;
}
.title {
  margin: 10px;
  color: #444;
  font-size: 150%;
  text-align: center;
}
.content {
  padding: 10px;
  color: #666;
}
</style>
