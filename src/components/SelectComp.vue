<template>

    <div>

        <!-- Select da cui l'utente puo scegliere il genere al click, il quale restituirà solo album del genere scelto -->
        <label for="" class="p_10 text_white">Search genre: </label>
        <select class="p_10 bg-custom-dark-blue b-rounded text_white b-none" 
                name="" 
                id=""
                @click.prevent="$emit('selectSearch', option.value)"
                >
            <optgroup label="Genre:">
                <option value="All">All</option>
                <option value="Rock">Rock</option>
                <option value="Pop">Pop</option>
                <option value="Jazz">Jazz</option>
                <option value="Metal">Metal</option>
            </optgroup>
        </select>

    </div>
    

</template>

<script>

export default {
  name: 'SelectComp',
  components: {
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/general.scss';

    
</style>