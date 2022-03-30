<template>
  <main>
    <div class="container">
      <div class="card" v-for="film in arraySearchFilm" :style=" 'background: url(\'http://image.tmdb.org/t/p/w200/' + film.poster_path + '\');'" :key="film.id">
        <div class="background">
          <div class="card-text">
            <div>Titolo: {{film.title}}</div>
            <div>Titolo originale: {{film.original_title}}</div>
            <lang-flag :iso="film.original_language"/>
            <div>Voto: {{film.vote_average}}</div>
          </div>
        </div>
      </div>
    </div>
    <div class="series"> Serie TV</div>
    <div class="container">
      <div class="card" v-for="sit in arraySearchTv" :style=" 'background: url(\'http://image.tmdb.org/t/p/w200/' + sit.poster_path + '\');'" :key="sit.id">
      <div class="background">
        <div class="card-text">
          <div>nome: {{sit.title}}</div>
          <div>Titolo originale: {{sit.original_title}}</div>
          <lang-flag :iso="sit.original_language" />
          <div>Voto: {{sit.vote_average}}</div>
        </div>
      </div>
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
.hidden{
  display: none;
}
.series{
  color: white;
  font-size: 2rem;
}
.card{
  position: relative;
  height: 300px;
  width: 200px;
  margin: 2rem;
  border-radius: .5rem;
  overflow: auto;
  color: white;
  border: 2px solid white;
  .card-text{
    height: 70%;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
  }
  .background{
    position: absolute;
    top: 0;
    z-index: 0;
    height: 100%;
    width: 100%;
    background-color: rgba($color: #000000, $alpha: 0.4);
  }
}
</style>
