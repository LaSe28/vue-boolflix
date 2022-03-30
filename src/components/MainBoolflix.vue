<template>
  <main>
    <div class="container">
      <div class="card" v-for="film in arraySearchFilm" :key="film.id">
        <div>Titolo: {{film.title}}</div>
        <div>Titolo originale: {{film.original_title}}</div>
        <lang-flag :iso="film.original_language"/>
        <div>Voto: {{film.vote_average}}</div>
      </div>
    </div>
    <div style="background-color: red;">serie tv</div>
    <div class="container">
      <div class="card" v-for="sit in arraySearchTv" :key="sit.id">
        <div>nome: {{sit.title}}</div>
        <div>Titolo originale: {{sit.original_title}}</div>
        <lang-flag :iso="sit.original_language" />
        <div>Voto: {{sit.vote_average}}</div>
      </div>
    </div>
  </main>
</template>

<script>
import LangFlag from 'vue-lang-code-flags'

export default {
  name: 'MainBool',
  components: {
    LangFlag
  },
  data () {
    return {
      lang: null
    }
  },
  props: {
    arraySearchFilm: Array,
    arraySearchTv: Array
  }
}
</script>

<style scoped lang="scss">
.container{
  display: flex;
  flex-wrap: wrap;
}
.card{
  height: 300px;
  width: 200px;
  margin: 2rem;
  overflow: auto;
  background-color: #c1c1c1;
  div{
    margin-bottom: 1rem;
  }
}
</style>
