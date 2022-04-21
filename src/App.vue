<template>

  <div>

      <header class="container_default">

        <HeaderComp
          v-for="(element, index) in albumsLibrary"
          :key="index"
          :image="element.poster"
          :author="element.author"
          :genre="element.genre"
          :title="element.title"
          :year="element.year"
        />

      </header>

      <main id="bodyMain" class="h-90-vh">

        <div id="library" class="container-default">

          <MainComp
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

      </main>

  </div>


</template>

<script>
import HeaderComp from './components/HeaderComp.vue';
import MainComp from './components/MainComp.vue';
import axios from 'axios';

export default {
  name: 'App',

  components: {
    HeaderComp,
    MainComp,
  },

  data() {
    return {
      albumsLibrary: [],
    }
  },

  created() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then( (res)  => {
      console.log( res.data.response )
      this.albumsLibrary = res.data.response;
    }
    )
    .catch( (error) => {
          console.log( error )
      })
  },

}
</script>

<style lang="scss">
@import './assets/style/general.scss';
@import url('https://fonts.googleapis.com/css2?family=Fira+Sans+Extra+Condensed&display=swap');

  body {
    font-family: 'Fira Sans Extra Condensed', sans-serif;
  }

  #bodyMain {
     background: $dark-blue-dark;
   }

   #library {
     @include flexRowWrap;
   }



</style>
