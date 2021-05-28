<template>
  <header class="container pt-5">
    <form class="d-flex pb-5  ">
      <div class="flex-grow-1 ">
        <input 
          @keyup.enter="startSearch('all')"
          v-model.trim="strToSearch"
          class="form-control" 
          type="text"
          placeholder="Cerca...">
      </div>
      <div>
        <button 
          class="btn btn-primary ms-3"
          @click.prevent="startSearch('movie')"
          >
          FILM
        </button>
      </div>
      <div>
        <button 
          class="btn btn-primary ms-3"
          @click.prevent="startSearch('tv')"
          >
          SERIE-TV
        </button>
      </div>
      <div>
        <button 
          class="btn btn-primary ms-3"
          @click.prevent="startSearch('all')"
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
    startSearch(type){
      this.$emit("searchFilm",{text:this.strToSearch,type:type})
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
  }
</style>