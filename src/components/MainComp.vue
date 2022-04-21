<template>

    <div id="bodyMain" class="h-90-vh">  
      
      <div id="library" class="container-default">

        <CardsComp
          class="p-20"
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
import axios from 'axios'
import CardsComp from './CardsComp.vue'


export default {
  name: 'MainComp',
  
  data() {
    return {
      albumsLibrary: [],
    }
  },

  components: {
    CardsComp,
  },
  
  created() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then( (res)  => {
      console.log( res.data.response )
      this.albumsLibrary = res.data.response;
      console.log(this.albumsLibrary);
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

   #library {
     @include flexRowAlignWrap;
   }

</style>
