<template>
  <div class="container">
    <form class="d-flex mb-5 mt-5">
      <div class="flex-grow-1 ">
        <input 
          @keyup.enter="startSearch"
          v-model.trim="strToSearch"
          class="form-control" 
          type="text"
          placeholder="Cerca Film">
      </div>
      <div>
        <button 
          class="btn btn-primary ms-3"
          @click.prevent="startSearch"
          >
          Cerca
        </button>
      </div>
    </form>
  </div>
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
    startSearch(){
      this.$emit("searchFilm",this.strToSearch)
    }
  }
}
</script>

<style lang="scss" scoped>
  
</style>