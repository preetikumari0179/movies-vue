<template>
  <div class="home">
    <div class="search-box">
      <span class="search-header">
      Search Your Movie Interest
      </span>
      <br/>
      <span class="search-desc">
      Search your movie using search box
      </span>
      <br/>
      <input placeholder="search" v-model="searchParam" class="Stroke-9" />
      <img src="../assets/fill-58.png" class="Fill-58">
      <br/>
      <button @click="search()" class="Stroke-15">
        Find
      </button>
      </div>
      <movie-carousel title="Search Results" :items="searchedMovies">
      </movie-carousel>
      <movie-carousel title="Popular Movies" :items="popularMovies">
      </movie-carousel>
      <movie-carousel title="Movies In Theatre" :items="moviesInTheatre">
      </movie-carousel>
  </div>
</template>

<script>

export default {
  name: 'home',
  data() {
    return {
      searchParam: '',
      movies: [],
    }
  },
  components: {
    'movieCarousel': () => import('../components/movieCarousel.vue')
  },
  methods: {
    search() {
      console.log(this.searchParam, 'search param')
      if (this.searchParam.length) {
        this.$store.dispatch('searchMovies', this.searchParam);
      }
    }
  },
  created() {
    console.log(this.$store);
    this.$store.dispatch('getPopularMovies');
    this.$store.dispatch('getMoviesInTheatre')
  },
  computed: {
    popularMovies() {
      return this.$store.state.popularmovies;
    },
    moviesInTheatre() {
      return this.$store.state.moviesintheatre
    },
    searchedMovies() {
      return this.$store.state.searchmovies
    }
  },
}
</script>
<style lang="css" scoped>
  .search-box {
    height: 180px;
    background-color: #24242c;
    padding: 5px;
    margin: 20px 0px 100px 10px;
  }
  .search-header {
     width: 122px;
    height: 41px;
    font-family: Helvetica;
    font-size: 33.7px;
    font-weight: bold;
    font-style: normal;
    font-stretch: normal;
    line-height: normal;
    letter-spacing: 0px;
    color: #69c297;
  }
  .search-desc {
     width: 175px;
  height: 26px;
  font-family: Helvetica;
  font-size: 22.4px;
  font-weight: normal;
  font-style: normal;
  font-stretch: normal;
  line-height: normal;
  letter-spacing: 0px;
  color: #d7ede5;
  padding: 4px

  }
  .Fill-58 {
    margin-left: -45px;
    top: 1px
}
.Stroke-9 {
  width: 983.6px;
  height: 48.1px;
  border: solid 1.5px #969696;
  border-radius: 5px
}
.Stroke-15 {
  width: 150px;
  height: 42.6px;
  border: solid 3px #5ec19e;
  background-color: #32313b;
  color: #d7ede5;
  border-radius: 5px;
  padding: 4px
}
</style>