<template>
  <main>
    <div class="card" v-for="film in textSearchFor" :key="film.title">
      <div>Titolo: {{film.title}}</div>
      <div>Titolo originale: {{film.original_title}}</div>
      <div>Trama: {{film.overview}}</div>
      <div>Voto: {{film.vote_average}}</div>

    </div>
  </main>
</template>

<script>

export default {
  name: 'MainBool',
  data () {
    return {
    }
  },
  props: {
    textSearchFor: Array
  },
  methods: {

  }
}
</script>

<style scoped lang="scss">
main{
  display: flex;
  flex-wrap: wrap;
}
.card{
  height: 300px;
  max-width: calc((100% / 6) - 2rem);
  min-width: 200px;
  margin: 2rem;
  overflow: auto;
  background-color: #c1c1c1;
  div{
    margin-bottom: 1rem;
  }
}
</style>
