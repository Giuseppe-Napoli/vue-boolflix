<template>
  <main class="container">
    <!--creo un h1 che mi stamperà un title in base al suo valore che dipenderà dal [type] se tittle è 'movie' avro un [type] altrimenti un altro -->
    <h1 v-if="listFilm.length > 0">{{title[type]}}</h1>


    <div class=" row">
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
        'movie': 'Film ',
        'tv': 'Serie-TV ',
      }
    }
  },

  methods: {
    titleNo(){
      if(this.listFilm.movie.lenght == 0){
        return "<h1>niente</h1>"
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
  main{
    margin-top: 70px;
    padding-top: 70px;
    h1{
      color:#e50914;
      margin: 0 0 50px 20px;
      text-transform: uppercase;
      font-weight: 900;
      font-size: 45px;
      text-shadow: 0 5px 8px black;
    }
  }
</style>