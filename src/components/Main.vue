<template>
  <main class="container mt-5">
    <div class="d-flex flex-wrap">
    <!-- ciclo i miei film nella listFilm e li stampo all'interno della main grazie al v-bind di film, precedentemente dichiarato nel comp film.vue attraverso il props-->
      <Film 
          v-for="(film, index) in listFilm"
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
    listFilm:Array
  },

    components: {
      Film,
  },




}
</script>

<style lang="scss" scoped>
  
</style>