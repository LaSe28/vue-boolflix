<template>
  <main :textSearchFor="searched()">
    <div v-for="film in arrSearch" :key="film.title">
      <div>{{film.title}}</div>
    </div>
  </main>
</template>

<script>
import axios from 'axios'

export default {
  name: 'MainBool',
  data () {
    return {
      arrSearch: []
    }
  },
  props: {
    textSearchFor: String
  },
  methods: {
    searched () {
      if (this.textSearchFor !== '') {
        console.log(this.textSearchFor)
        axios.get(`https://api.themoviedb.org/3/search/movie?api_key=01af620fbe2924c05e6048caa6f5c225&query=${this.textSearchFor}`)
          .then((res) => {
            console.log(res.data.results)
            for (let i = 0; i < res.data.results.length; i++) {
              this.arrSearch.push({
                title: res.data.results[i].title,
                overview: res.data.results[i].overview,
                poster_path: res.data.results[i].poster_path,
                original_title: res.data.results[i].original_title
              })
            }
            console.log(this.arrSearch)
          })
      }
    }
  }
}
</script>

<style>

</style>
