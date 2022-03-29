<template>
  <main>
    <p :textSearchFor="searched()"></p>
  </main>
</template>

<script>
import axios from 'axios'

export default {
  name: 'MainBool',
  data () {
    return {
      searchedFor: ''
    }
  },
  props: {
    textSearchFor: String
  },
  methods: {
    searched () {
      if (this.searchedFor !== '') {
        console.log(this.textSearchFor)
        axios.get(`https://api.themoviedb.org/3/search/movie?api_key=01af620fbe2924c05e6048caa6f5c225&query=${this.textSearchFor}`)
          .then((res) => console.log(res.data.results))
      }
    }
  }
}
</script>

<style>

</style>
