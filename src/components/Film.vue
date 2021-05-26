<template>
  <div class="disc mb-5 p-3 text-center">
    <div class="film mb-5 p-3 ">
      <h2>Titolo: {{film.title}}</h2>
      <h3>Titolo Originale: {{film.original_title}}</h3>
      <div class="mt-3 mb-2">
        <h4>Lingua: {{film.original_language}}</h4>
        <img :src="bandiera()" alt="">
      </div>
      <h5>Voto: {{film.vote_average}}</h5>
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
    // prova funzione per bandiere
    bandiera(){

      if(this.film.original_language === "it"){
        return require(`../assets/img/italy.png`)
      }

      else if(this.film.original_language === "en"){
        return require(`../assets/img/english.png`)
      }

      else if(this.film.original_language === "es"){
        return require(`../assets/img/espana.png`)
      }

      else if(this.film.original_language === "de"){
        return require(`../assets/img/germany.png`)
      }

      else if(this.film.original_language === "fr"){
        return require(`../assets/img/france.svg`)
      }
      else{
        return null
      }
    }
  },

  created(){
    
      console.log('--ling-->',this.film.original_language)
    
  }
  
}
</script>

<style lang="scss" scoped>
  .disc{
  flex-basis: calc(100% / 3);
  .film{
    background-color: rgba(0,0,0,0.2);
    border-radius: 10px;
    min-height: 380px;
    h2{
      color: brown
    }
    h3{
      color:rgb(231, 156, 57)
    }
    h4{
      color:cornflowerblue
    }
    img{
      width: 80px;
      height: 40px;
    }
  }
}
</style>