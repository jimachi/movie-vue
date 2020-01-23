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
    <div v-for="movie in movies.Search" :class="card" :key="movie">
      <img :src=movie.Poster :alt=movie.Title>
      <div class="container">
        <h4><b>{{ movie.Title }}</b></h4>
      </div>
    </div>
    
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
#app {
  background-color: #ededed;
}

.card {
  box-shadow:0 4px 8px rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  width: 40%;
}
img {
  width: 250px;
}
.container {
  padding: 2px 16px;
}
.card:hover {
  box-shadow:0 8px 16px rgba(0, 0, 0, 0.2);
}
</style>
