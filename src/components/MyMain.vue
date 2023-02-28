<template>
  <div>
      <section class="movie">
          <h2>Elenco dei film</h2>

          <ul class="card">
            
            <MyFilm v-for="(film, index) in filmList" :key="index" :item="film"/>
          </ul>
      </section>

      <section class="series">
          <h2>Elenco dei serie</h2>

          <ul>
            <li>Cover - Titolo - Titolo originale - Lingua - Voto</li>
            <MyFilm v-for="(serie, index) in seriesList" :key="index" :item="serie"/>
          </ul>
      </section>
  </div>
</template>

<script>
import MyFilm from './MyFilm.vue';
export default {
    name: 'MyMain',
    props: {
    filmList: Array,
    seriesList: Array,
    },
    components:{
        MyFilm,
    }
}
</script>

<style lang="scss">

.flag{
    max-width:  30px;
}
</style>