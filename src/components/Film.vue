<template>
  <div class="disc mb-4 p-2 text-center">
    <div class="film mb-4 p-2 ">
      <h2 class="mb-2">Titolo: {{film.title || film.name}}</h2>
      <img :src="getImg(film.poster_path)" alt="">
      <h3>Titolo Originale: {{film.original_title || film.original_name}}</h3>
      <div class="lang mt-2 mb-2">
        <h4 v-if="this.film.original_language !== 'en' && this.film.original_language !== 'it'">Lingua: {{film.original_language}}</h4>
        <img v-if="this.film.original_language == 'en' || this.film.original_language == 'it'" :src="bandiera()" alt="Bandiera">
      </div>
      <h5>Voto: {{getVoto()}}</h5>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Film',
  /* col props mi viene passato l'array di oggetti dal Main.vue a questo punto nel mio template sarò in grado di passare gli elementi dell'array che mi interessano*/
  props:{
    film: Object
  },
  methods: {
    //funzione che mi ritorna il voto da 1 a 5
    getVoto(){
      return Math.ceil((this.film.vote_average * 5) / 10)
    },
    //funzione che mi ritorna l'immagine, concateno url che nel bind dell'img avrà il valore di film.poster_path
    getImg(url){
      return "https://image.tmdb.org/t/p/w342"+url
    },
    // prova funzione per bandiere
    bandiera(){

      if(this.film.original_language === "it"){
        return require(`../assets/img/it.png`)
      }

      else if(this.film.original_language === "en"){
        return require(`../assets/img/en.png`)
      }

      /* else if(this.film.original_language === "es"){
        return require(`../assets/img/espana.png`)
      }

      else if(this.film.original_language === "de"){
        return require(`../assets/img/germany.png`)
      }

      else if(this.film.original_language === "fr"){
        return require(`../assets/img/france.svg`)
      } */
      else{
        return null
      }
    }
  },

  created(){
    
  }
  
}
</script>

<style lang="scss" scoped>
  .disc{
  flex-basis: calc(100% / 3);
  .film{
    background-color: rgba(0,0,0,0.2);
    border-radius: 10px;
    min-height: 500px;
    h2{
      color: brown
    }
    h3{
      color:rgb(231, 156, 57)
    }
    img{
      width: 200px;
    }
    .lang{
      h4{
        color:cornflowerblue
      }
      img{
        width: 70px;
        height: 30px;
      }

    }
  }
}
</style>