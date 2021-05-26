<template>
  <main class="container mt-5">
    <div class="d-flex flex-wrap">
    <!-- ciclo i miei film nella listFilm (successivamente filtrato e diventato filterFilm) e li stampo all'interno della main grazie al v-bind di film, precedentemente dichiarato nel comp film.vue attraverso il props-->
      <Film 
          v-for="(film, index) in filterFilm"
          :key="index"
          :film="film" />
    </div>
  </main>
</template>

<script>

import Film from './Film'

export default {
  name: 'Main',
  props:{
    filterFilm:Array
  },

    components: {
      Film,
  },




}
</script>

<style lang="scss" scoped>
  
</style>