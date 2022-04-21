<template>

        <div id="cont">
          
          <img :src="image" alt="Foto album">
          <div class="list author">{{author}}</div>
          <div class="list">{{title}}</div>
          <div class="list">{{genre}}</div>
          <div class="list">{{year}}</div>
            
        </div>

</template>

<script>


export default {
  name: 'MainComp',

  props: {
    author: String,
    genre: String,
    image: String,
    title: String,
    year: String,
  },

  components: {
  },
  

}
</script>

<style lang="scss" scoped>
@import '../assets/style/general.scss';

  img {
      width: 140px;
      height: 140px;
      margin: 0 auto;
    }

    .list {
      margin: 0 auto;
      padding: 5px;
      
    }

    #cont {
      vertical-align: middle;
      width: 160px;
      color: white;
      background-color: $dark-blue;
      margin: 10px;
      display: flex;
      flex-direction: column;
      justify-content: center;
    }

    .author {
      text-transform: uppercase;
      font-weight: bold;
      margin-top: 5px;
    }

</style>
