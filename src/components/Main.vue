<template>
  <main class="container">
    <!--creo un h1 che mi stamperà un title in base al suo valore che dipenderà dal [type] se tittle è 'movie' avro un [type] altrimenti un altro -->
    <h1>{{title[type]}}</h1>

    <!-- ciclo i miei film nella listFilm e li stampo all'interno della main grazie al v-bind di film, precedentemente dichiarato nel comp film.vue attraverso il props-->
    <!-- <i @click="scroll_left()" class="fas fa-chevron-left"></i> -->
        <div v-if="listFilm.length > 0">
          <VueSlickCarousel :arrows="true" :dots="true" v-bind="settings">
            <Film 
                v-for="film in listFilm"
                :key="film.id"
                :film="film" />
          </VueSlickCarousel>
        </div>
        
     <!--  <i @click="scroll_right()" class="fas fa-chevron-right"></i> -->
  </main>
</template>

<script>

import Film from './Film';
import VueSlickCarousel from 'vue-slick-carousel';
import 'vue-slick-carousel/dist/vue-slick-carousel.css';
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css';

export default {
  name: 'Main',
    components: {
      Film,
      VueSlickCarousel
  },
  
  data(){
    return{
      title:{
        'movie': 'Film ',
        'tv': 'Serie-TV ',
      },
      settings:{

        "centerMode": true,
        "centerPadding": "10%",
        "focusOnSelect": true,
        "infinite": true,
        "slidesToShow": 4,
        "speed": 500,
        "responsive": [
          {
            "breakpoint": 1400,
            "settings": {
              "slidesToShow": 3.5,
            }
          },

          {
            "breakpoint": 1200,
            "settings": {
            "slidesToShow": 3,
            "centerPadding": "8%",
            "arrows":false
            }
          },
          {
            "breakpoint": 990,
            "settings": {
            "slidesToShow": 2.5,
            "centerPadding": "3%",
            "arrows":true
            }
          },
          {
            "breakpoint": 770,
            "settings": {
            "slidesToShow": 2,
            "centerPadding": "2%",
            "arrows":true
            }
          },
          {
            "breakpoint": 580,
            "settings": {
            "slidesToShow": 1.5,
            "centerPadding": "7%",
            "arrows":false
            }
          },
          {
            "breakpoint": 450,
            "settings": {
            "slidesToShow": 1.5,
            "centerPadding": "5%",
            "arrows":false
            }
          },
          {
            "breakpoint": 375,
            "settings": {
            "slidesToShow": 1,
            "centerPadding": "5%",
            "arrows":false
            } 
          }
        ]
      }
      
    }
  },


  methods: {
/*     scroll_right() {
      let content = document.querySelector(".wrap");
      content.scrollLeft += 400;
    
    },
  scroll_left() {
    let content = document.querySelector(".wrap");
    content.scrollLeft -= 400;
  } */
},
  props:{
    listFilm:Array,
    type:String
  },






}
</script>

<style lang="scss" scoped>
  main{
    margin-top: 70px;
    padding-top: 70px;
/*     .slide{
      position: relative;
      overflow: hidden;
      .fas{
        position:absolute;
        top: 250px;
        font-size: 40px;
        font-weight: 800;
        cursor: pointer;
        
      }
      .fa-chevron-left{
        left: 20px;
        &:hover{
          left: 16px;
          font-size: 44px;
        }
      }
      .fa-chevron-right{
        left: 96%;
        &:hover{
          left: 96.1%;
          font-size: 44px;
        }
      }
    }
    .wrap{
      display: flex;
      flex-wrap: nowrap;
      flex-direction: row;
      padding-top: 40px;
      width: 92%;
      margin-left: 70px;
      overflow-x: hidden;
    } */
    h1{
      color:#e50914;
      margin: 0 0 15px 15px;
      text-transform: uppercase;
      font-weight: 900;
      font-size: 55px;
      text-shadow: 0 5px 8px black;
    }
    .slick-prev:before, .slick-next:before {
    font-family: 'slick';
    font-size: 50px;
    line-height: 1;
    opacity: 0.75;
    color: rgb(177, 32, 32);
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}
  }
</style>