<template>
  <main class="container-fluid mt-5">
    <!--creo un h1 che mi stamperà un title in base al suo valore che dipenderà dal [type] se tittle è 'movie' avro un [type] altrimenti un altro -->
    <h1>{{title[type]}}: <span>{{listFilm.length}}</span></h1>
    

    <div class="d-flex flex-wrap">
    <!-- ciclo i miei film nella listFilm e li stampo all'interno della main grazie al v-bind di film, precedentemente dichiarato nel comp film.vue attraverso il props-->
      <Film 
          v-for="film in listFilm"
          :key="film.id"
          :film="film" />
    </div>
  </main>
</template>

<script>

import Film from './Film'

export default {
  name: 'Main',
  data(){
    return{
      title:{
        'movie': 'Film Trovati',
        'tv': 'Serie-TV Trovate',
      }
    }
  },
  props:{
    listFilm:Array,
    type:String
  },

    components: {
      Film,
  },




}
</script>

<style lang="scss" scoped>
  
</style>