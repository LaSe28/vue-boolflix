<template>
  <div id="app">
    <HeaderBool @search="searchTitle" />
    <MainBool :arraySearchFilm="arrSearchFilm" :arraySearchTv="arrSearchTv" />
  </div>
</template>

<script>
import HeaderBool from './components/HeaderBoolflix.vue'
import MainBool from './components/MainBoolflix.vue'
import axios from 'axios'

export default {
  name: 'App',
  data () {
    return {
      searchValue: '',
      arrSearchFilm: [],
      arrSearchTv: []
    }
  },
  components: {
    HeaderBool,
    MainBool
  },
  methods: {
    searchTitle (searchValue) {
      this.arrSearchFilm = []
      this.arrSearchTv = []
      this.searchValue = searchValue
      if (this.searchValue !== '') {
        axios.get(`https://api.themoviedb.org/3/search/movie?api_key=01af620fbe2924c05e6048caa6f5c225&language=it_IT&query=${this.searchValue}`)
          .then((res) => {
            for (let i = 0; i < res.data.results.length; i++) {
              this.arrSearchFilm.push({
                title: res.data.results[i].title,
                poster_path: res.data.results[i].poster_path,
                original_title: res.data.results[i].original_title,
                original_language: res.data.results[i].original_language,
                vote_average: res.data.results[i].vote_average
              })
            }
            return this.arrSearchFilm
          })
        axios.get(`https://api.themoviedb.org/3/search/tv?api_key=01af620fbe2924c05e6048caa6f5c225&language=it_IT&query=${this.searchValue}`)
          .then((res) => {
            console.log(res)
            for (let i = 0; i < res.data.results.length; i++) {
              this.arrSearchTv.push({
                title: res.data.results[i].name,
                poster_path: res.data.results[i].poster_path,
                original_title: res.data.results[i].original_name,
                original_language: res.data.results[i].original_language,
                vote_average: res.data.results[i].vote_average
              })
            }
          })
      }
    }

  }
}
</script>

<style lang="scss">

</style>
