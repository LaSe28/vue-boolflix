<template>
<main>
<div v-if="arraySearchFilm.length !== 0" class="type">Film ({{arraySearchFilm.length}})</div>
<div class="container">
  <div class="flip-card" v-for="film in arraySearchFilm"  :key="film.id">
    <div class="in-card">
      <div class="default" v-if="film.poster_path === null">
        <img src="../assets/img/no-image.png" alt="">
      </div>
      <div v-else class="front-card" :style=" 'background: url(\'http://image.tmdb.org/t/p/w342/' + film.poster_path + '\');'"></div>
      <div class="back-card">
        <h3>Titolo: {{film.title}}</h3>
        <h4>Titolo originale: {{film.original_title}}</h4>
        <span><i v-for="star in Math.ceil(film.vote_average / 2)" :key="star.index" class="fa-solid fa-star"></i></span>
        <lang-flag :iso="film.original_language"/>
      </div>
    </div>
  </div>
</div>
<div v-if="arraySearchTv.length !== 0" class="type">Film ({{arraySearchTv.length}})</div>
<div class="container">
  <div class="flip-card" v-for="sit in arraySearchTv"  :key="sit.id">
    <div class="in-card">
      <div class="default" v-if="sit.poster_path === null">
        <img src="../assets/img/no-image.png" alt="">
      </div>
      <div v-else class="front-card" :style=" 'background: url(\'http://image.tmdb.org/t/p/w342/' + sit.poster_path + '\');'"></div>
      <div class="back-card">
        <h3>Titolo: {{sit.title}}</h3>
        <h4>Titolo originale: {{sit.original_title}}</h4>
        <span><i v-for="star in Math.ceil(sit.vote_average / 2)" :key="star.index" class="fa-solid fa-star"></i></span>
        <lang-flag :iso="sit.original_language"/>
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
  },
  methods: {
  }
}
</script>

<style scoped lang="scss">
.container{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.flip-card {
  background-color: transparent;
  width: 342px;
  height: 500px;
  perspective: 1000px;
  margin: 1rem;
  border:2px solid white ;
  border-radius: .5rem;
  overflow: hidden;
  }

.in-card {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.6s;
  transform-style: preserve-3d;
}

.flip-card:hover .in-card {
  transform: rotateY(180deg);
}

.default{
  position: absolute;
  text-align: center;
  height: 100%;
  background-color: #F8F8F9;
  img{
    width: 80%;
  }
}

.front-card, .back-card {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.front-card {
  color: black;
}

.back-card {
  display: flex;
  flex-direction: column;
  color: white;
  transform: rotateY(180deg);
  background-color: black;
  h3{
    margin: 1rem;
    font-size: 2rem;
  }
  h4{
    margin: 2rem 1rem;
    font-size: 1.5rem;
  }
}
.type{
  color: white;
  font-size: 2rem;
  margin: 2rem;
}
span{
  margin: 1rem;
}
.fa-solid{
  font-size: 2rem;
  display: inline-block;
  color: yellow;
}
</style>
