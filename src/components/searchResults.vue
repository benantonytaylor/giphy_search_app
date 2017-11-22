<template>
  <div class="search_results_container" >
    <div v-for="image in images">
      <ImageColumn  v-bind:image="image" />
    </div>
  </div>
</template>

<script>
import ImageColumn from './imageColumns'

export default {
  name: 'SearchResults',
  components: {
    ImageColumn
  },
  props: ['images'],
  data () {
    return {
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

.search_results_container {
  max-width: 900px;
  margin: 2em auto;
  display: grid;
  grid-gap: 1em;
  grid-template-columns: 1fr;
  grid-template-rows: auto auto auto auto;
}
@media screen and (min-width:900px) {
  .search_results_container {
    grid-template-columns: 1fr 1fr 1fr 1fr;
    grid-template-rows: auto;
  }
}
</style>
