<template>
  <div class="disc flip-card text-center">
    <div class=" mb-5 p-2  d-flex justify-content-center align-items-center flip-card-inner">
      <div class=" flip-card-front">
        <img class="p-3" v-if="this.film.poster_path !== null" :src="getImg(film.poster_path)" :alt="film.title||film.name">
        <div v-if="this.film.poster_path == null" class="box-undefined text-uppercase">--err--</div>
      </div>
      <div class="flip-card-back d-flex justify-content-center flex-column p-5">
        <ul>
          <li>
            Titolo: {{film.title || film.name}}
          </li>
          <li>
            Titolo Originale: {{film.original_title || film.original_name}}
          </li>
          <li class="d-flex justify-content-center">
            Lingua: <flag :iso="transformBand()"/>
          </li>
          <li class="d-flex justify-content-center">
            Voto: <Rating :grade= getVoto() :maxStars="5" />
          </li>
        </ul>
      
  <!-- <div class="lang mt-2 mb-2">
        <h4 v-if="this.film.original_language !== 'en' && this.film.original_language !== 'it'">Lingua: {{film.original_language}}</h4>
        <img v-if="this.film.original_language == 'en' || this.film.original_language == 'it'" :src="bandiera(film.original_language)" alt="Bandiera">
      </div> -->

      </div>
    </div>
  </div>
</template>

<script>
import Rating from './Rating.vue'
export default {
  name: 'Film',
  components: {
    Rating
  },
    beforeCreate: function() {
    document.body.className = 'home';
  },
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

    //  funzione per bandiere per it o en
/*     bandiera(ind){

      if(this.film.original_language === "it" || this.film.original_language === "en"){
        return require("../assets/img/"+ind+".png")
      }

    }, */

       //  funzione per bandiere per 'tutte''

      transformBand(){
      if (this.film.original_language === 'en'){
        return  'gb'
      } 
      else if (this.film.original_language === 'ja') {
        return 'jp'
      } 
      else if (this.film.original_language === 'he') {
        return 'il'
      } 
      else if (this.film.original_language === 'zh') {
        return 'cn'
      } 
      else if (this.film.original_language === 'hi') {
        return 'in'
      } 
      else if (this.film.original_language === 'cs') {
        return 'cz'
      } 
      else if (this.film.original_language === 'ar') {
        return 'sa'
      } 
      else if (this.film.original_language === 'sv') {
        return 'se' 
      } 
      else if (this.film.original_language === 'ko') {
        return 'kr'
      } 
      else {
        return this.film.original_language
      }
    } 
  },

  created(){
    
  }
  
}
</script>

<style lang="scss" scoped>

  @import '../assets/style/flipCard.scss';



  .disc{
  flex-basis: calc((100%  / 4) - 20px);
  margin: 0 10px;

 
    

    .flag-icon-gb.flag-icon-squared{
      width: 22px;
      margin-bottom: 2px;
    }
    .box-undefined{
      width: 100%;
      height: auto;
      margin: 25px ;
      border-radius: 10px;
      line-height: 300px;
      background-color: rgba(245, 239, 239, 0.7);
      text-align: center;
    }
      /*     .lang{
      h4{
        color:cornflowerblue
      }
      img{
        width: 70px;
        height: 30px;
      }

    } */
}
</style>