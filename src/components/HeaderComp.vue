<template>

    <div class="bg-custom-blue h-10-vh d_flex justify_between">

      <div  class="d_flex align_center">
        
        <img src="../assets/img/logo-spotify.png" alt="" class="p-x-15">

      </div>

      <div class="d_flex align_center p-20">

        <SearchBar @functionSearch="searchFunction" />

      </div>

      <div class="d_flex align_center p-20">

        <SelectComp @selectSearch="searchSelect" />

      </div>

    </div>
    

</template>

<script>
import SelectComp from './SelectComp.vue'
import SearchBar from './SearchBar.vue'

export default {
  name: 'HeaderComp',
  components: {
    SelectComp,
    SearchBar,
  },

  props: {
    author: String,
    genre: String,
    image: String,
    title: String,
    year: String,
  },

  data() {
    return {
      dataLibrary: [],
    }
  },

  computed: {
    // filterFunction() {
      // qui metto la funzione che filtra il vecchio array con il nuovo array dataLibrary 
    // }
  },

  created() {
    
  },

  methods: {
    searchSelect( select ) {
      // Il parametro select in questo caso sarebbe la variabile value creata nel figlio
      this.dataLibrary = select;
      
    }
  },
}
</script>

<style lang="scss" scoped>
@import '../assets/style/general.scss';

  img {
        width: 50px;
        height: 50px;
    }
    
</style>
        