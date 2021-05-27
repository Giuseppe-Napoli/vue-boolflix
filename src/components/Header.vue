<template>
  <header class="container">
    <form class="d-flex mb-5 mt-5 pt-3">
      <div class="flex-grow-1 ">
        <input 
          @keyup.enter="allSearch"
          v-model.trim="strToSearch"
          class="form-control" 
          type="text"
          placeholder="Cerca...">
      </div>
      <div>
        <button 
          class="btn btn-primary ms-3"
          @click.prevent="filmSearch"
          >
          FILM
        </button>
      </div>
      <div>
        <button 
          class="btn btn-primary ms-3"
          @click.prevent="tvSearch"
          >
          SERIE-TV
        </button>
      </div>
      <div>
        <button 
          class="btn btn-primary ms-3"
          @click.prevent="allSearch"
          >
          TUTTO
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
    }
  },

  methods:{
    filmSearch(){
      this.$emit("searchFilm",{text:this.strToSearch,type:'movie'})
    },
    tvSearch(){
      this.$emit("searchFilm",{text:this.strToSearch,type:'tv'})
    },
    allSearch(){
      this.$emit("searchFilm",{text:this.strToSearch,type:'all'})
    }
  }
}
</script>

<style lang="scss" scoped>
  header{
    height: 70px;
    background-color: rgba(0,0,0,0.5);
  }
</style>