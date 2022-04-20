<template>

    <div id="bodyMain" class="h-90-vh ">  
      
      <div class="container-default">

        <CardsComp
          v-for="(element, index) in albumsLibrary"
          :key="index"
          :image="element.poster"
          :author="element.author"
          :genre="element.genre"
          :title="element.title"
          :year="element.year"
        />

      </div>

    </div>

</template>

<script>
import CardsComp from './CardsComp.vue'
import axios from 'axios';

export default {
  name: 'MainComp',
  components: {
    CardsComp,
  },
  data() {
    return {
      albumsLibrary: [],
    }
  },
  created() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then( (res)  => {
      console.log( res.data )
      this.albumsLibrary = res.data;
    }
    )
    .catch( (error) => {
          console.log( error )
      })
  },
}
</script>

<style lang="scss" scoped>
@import '../assets/style/general.scss';

   #bodyMain {
     background: $dark-blue-dark;
   }

</style>
