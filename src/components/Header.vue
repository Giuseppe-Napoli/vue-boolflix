<template>
  <header class="container-fluid">
    <div class="ps-5">
      <a href="/">
        <img class="float-start" src="../assets/img/logo.png" alt="logo_netflix">
      </a>
      
    </div>
    <form class="d-flex float-end">
      <div class="flex-grow-1">
        
        <input 
          @keyup.enter="startSearch('all')"
          v-model.trim="strToSearch"
          class="form-control float-end" 
          type="text"
          placeholder="Cerca...">

      </div>
      <div>
        <button 
          class="btn red-btn-gn ms-2"
          @click.prevent="startSearch('movie')"
          >
          FILM
        </button>
      </div>
      <div>
        <button 
          class="btn red-btn-gn ms-2"
          @click.prevent="startSearch('tv')"
          >
          TV
        </button>
      </div>

    </form>
  </header>
</template>

<script>
export default {
  name: 'Header',

  data(){
    return{
      strToSearch: '',
      modal: false
    }
  },

  methods:{
    startSearch(type){
      this.$emit("searchFilm",{text:this.strToSearch,type:type})
    },
    
   
  }
}
</script>

<style lang="scss" scoped>
  header{
    position: fixed;
    top:0;
    z-index: 999;
    height: 70px;
    padding-top: 15px;
    background-color: rgba(0, 0, 0, 0.9);
    img{
      width: 150px;
    }
    form{
      width: 30%;
      display: block;
      
      .fa-search{
        color: #e50914;
        margin: 10px;
        font-size: 20px;
        cursor: pointer;

      }
      input{
        width: 80%;
      }
    }
    .red-btn-gn{
      background-color: #e50914;
      line-height: normal;
      padding: 7px 17px;
      font-weight: 400;
      font-size: 1rem;
      color: #fff;
      border-radius: 3px;
      &:hover{
        background-color: #ff0e1a;
        transform: scale(1.05);
      }
    }
  }
</style>