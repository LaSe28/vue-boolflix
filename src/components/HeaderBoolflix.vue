<template>
  <header>
    <h1>boolflix</h1>
    <div>
      <input @keydown.enter="searchFor" v-model="searchText" type="text">
      <button @click="searchFor">Cerca</button>
    </div>
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

<style lang="scss" scoped>
header{
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 5rem;
  background-color: black;
  h1{
    text-transform: uppercase;
    color: red;
    margin: 1rem;
  }
  input{
    height: 1.5rem;
  }
  button{
    margin: 1rem;
  }
}
</style>
