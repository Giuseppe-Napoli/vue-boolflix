<template>
  <div class="disc mb-5 p-3 text-center">
    <div class=" mb-5 p-3 ">
      <h2>Titolo: {{film.title}}</h2>
      <h3>Titolo Originale: {{film.original_title}}</h3>
      <h4>Lingua: {{film.original_language}}</h4>
      <h5>Voto: {{film.vote_average}}</h5>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Film',
  /* col props mi viene passato l'array di oggetti dal Main.vue a questo punto nel mio template sarò in grado di passare gli elementi dell'array che mi interessano*/
  props:{
    film: Object,
  }
}
</script>

<style lang="scss" scoped>
  .disc{
  flex-basis: calc(100% / 3);
  div{
    background-color: rgba(0,0,0,0.2);
    border-radius: 10px;
    h2{
      color: brown
    }
    h3{
      color:rgb(231, 156, 57)
    }
    h4{
      color:cornflowerblue
    }
  }
}
</style>