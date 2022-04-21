<template>

    <div>
        <!-- Searchbar che mi restituirà l'artista che scriverò -->
        <form action="" class="">
            <input type="text" 
                   class="form-control" 
                   placeholder="Search artist..."
                   v-model.trim="inputText"
                   >
            <button 
                @click.prevent="$emit('functionSearch',inputText)"
                :keyup="$emit('functionSearch',inputText)"
            >
            Search artist</button>
        </form>

    </div>
    

</template>

<script>

export default {
  name: 'SearchBar',
  components: {
  },
  data() {
      return {
          inputText: '',
      }
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/general.scss';

    
</style>