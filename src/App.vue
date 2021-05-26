<template>
  <div id="app">
    <Header 
    @searchFilm='searching'
    />
    <!-- chiamando l'API nel App.vue dovro passare l'array listFilm*  nella props della Main.vue a quel punto ciclerò tutti i film che mi ritorneranno indietro grazie al bind di listFilm* 
    * = l'array originale che prima era listFilm verrà filtrato all'interno di computed e trasformato in filterFilm-->
    <Main 
    :filterFilm="filterFilm"/>
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
      apiURL: 'https://api.themoviedb.org/3/search/movie',
      api_key: '6dfd8194553fe1b84032137a9761e594',
      query: 'madagascar',
      listFilm: [],
      textToSearch:'',

    }
    
  },
   methods: {
     searching(txt){
       this.textToSearch = txt;
     }
    // axios va messo qui dentro una funzione callApi()
    
  },
      
  computed: {
    filterFilm(){
      let cleanFilm = this.listFilm.filter(item => item.title != undefined)
      if(this.textToSearch === ""){
        return cleanFilm;
      }
      return cleanFilm.filter(item => item.title.toLowerCase().includes(this.textToSearch.toLowerCase()))
    }
  },

    created(){
      axios.get(this.apiURL,{
        params:{
          api_key: this.api_key,
          query: this.query,
          language: 'it-IT'
        }
      })
      .then(resp =>{
        this.listFilm = resp.data.results
        console.log('---->',this.listFilm);
      })
      .catch(err => {
        console.log(err);
      })
  },




 
}
</script>

<style lang="scss">
  @import './assets/style/general.scss'

</style>
