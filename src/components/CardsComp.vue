<template>

    <div>
        
          <img :src="image" alt="Foto album">
          <span>{{author}}</span>
          <span>{{genre}}</span>
          <div>{{title}}</div>
          <span>{{year}}</span>
          

    </div>

</template>

<script>

export default {
  name: 'CardsComp',
  props: {
    author: String,
    genre: String,
    image: String,
    title: String,
    year: String,
  },
}

</script>

<style lang="scss" scoped>
@import '../assets/style/general.scss';

    

</style>
