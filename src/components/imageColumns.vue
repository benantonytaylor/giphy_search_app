<template>
  <div class="image_column">
      <div class="image-div" v-for="img in image" v-bind:key="img.id">
        <img :src="img.images.fixed_width.url" alt="" >
      </div>
  </div>
</template>

<script>
export default {
  name: 'ImageColumn',
  props: ['image'],
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

.image_column {
  display: grid;
  grid-gap: 1em;
  grid-template-columns: auto;
  grid-template-rows: auto auto auto auto auto auto auto auto auto;
  justify-items: center;
  align-items: stretch;
}

@media screen and (min-width:650px) {
  .image_column {
     grid-template-columns: auto auto auto;
    grid-template-rows: auto auto auto;
    align-items: center;
  }
}

@media screen and (min-width:900px) {
  .image_column {
    grid-template-columns: auto;
    grid-template-rows: auto auto auto auto auto auto auto auto auto;
  }
}
.image_column img {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}



.image-div {
  position: relative;
}

.image-div:hover img {
  box-shadow: 0 4px 15px 2px rgba(153, 51, 255, 0.2), 0 6px 25px 2px rgba(153, 51, 255, 0.19);
  border: 2px solid rgb(153, 51, 255);
}

</style>
