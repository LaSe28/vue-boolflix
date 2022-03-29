<template>
  <div id="app">
    <HeaderBool @search="searchTitle"/>
    <MainBool :textSearchFor="searchValue"/>
  </div>
</template>

<script>
import HeaderBool from './components/HeaderBoolflix.vue'
import MainBool from './components/MainBoolflix.vue'

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
    }
  }
}
</script>

<style lang="scss">

</style>
