<template>
  <div id="app">

    <Header 
    @searchFilm='searching'
    />
    <!-- chiamando l'API nel App.vue dovro passare l'array listFilm nella props della Main.vue a quel punto ciclerò tutti i film che mi ritorneranno indietro grazie al bind di listFilm-->
    <!-- main per film che mostrerò solo se avrà un contenuto  -->
    <Main 
    v-if="listFilm.movie.length > 0" 
    :listFilm="listFilm.movie"
    type='movie'/>

    <!-- main per serie-tv che mostrerò solo se avrà un contenuto -->
    <Main 
    v-if="listFilm.tv.length > 0"
    :listFilm="listFilm.tv"
    type='tv'/>

  </div>
  
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },


  data(){
    return{
      apiURL: 'https://api.themoviedb.org/3/search/',
      api_key: '6dfd8194553fe1b84032137a9761e594',
      //lista che contiene un array di movie e una di serie tv
      listFilm:{
        movie:[],
        tv:[]
      },
      textToSearch:'',

    }
    
  },
   methods: {
     /* gli passo un obj che attraverso l'emit fatto sul header memorizzerà i valori di text e type provenienti da header.vue */
     searching(obj){
       this.resetArr();
       if(obj.type === 'all'){
         this.getApi(obj.text, 'movie');
         this.getApi(obj.text, 'tv');
       }else{
         this.getApi(obj.text, obj.type);
       }
      
     },
     //funzione per resettare gli array
     resetArr(){
       this.listFilm.movie= [],
       this.listFilm.tv= []
     },

     getApi(query, type){
       /* chiamata API, passando query e type. Query corrispondere al nostro v-model dell'input (infatti faremo la chiamata solo quanto il suo valore non sarà vuoto) nel header e type sarà quella stringa che nei componenti assumerà un valore tra 'movie' 'tv' 'all'   */
       if(query !== ''){
        axios.get(this.apiURL+type,{
          params:{
            api_key: this.api_key,
            query: query,
            language: 'it-IT',
          }
        })
        .then(res =>{
          this.listFilm[type] = res.data.results
          console.log('---->',this.page);
        })
        .catch(err => {
          console.log(err);
        })
       }
     },
  },
      
 
}
</script>

<style lang="scss">
  @import './assets/style/general.scss';

  body{
    background-image: url('~@/assets/img/netflix.jpg');
    height: 100vh;
  }

</style>
