<template>
  <header>
    <input v-model="searchText" type="text">
    <button @click="searchFor">Cerca</button>
  </header>
</template>

<script>

export default {
  name: 'HeaderBool',
  data () {
    return {
      searchText: ''
    }
  },
  components: {
  },
  methods: {
    searchFor () {
      const linkText = this.searchText.split(' ').join('+')
      this.$emit('search', linkText)
    }
  }
}
</script>

<style>

</style>
