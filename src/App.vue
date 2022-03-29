<template>
  <div id="app">
    <HeaderBool @search="searchTitle"/>
    <MainBool :textSearchFor="searchValue"/>
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
      searchValue: ''
    }
  },
  components: {
    HeaderBool,
    MainBool
  },
  methods: {
    searchTitle (searchValue) {
      this.searchValue = searchValue
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=01af620fbe2924c05e6048caa6f5c225&query=${this.searchValue}`)
        .then((res) => console.log(res.data.results))
    }
  }
}
</script>

<style lang="scss">

</style>
