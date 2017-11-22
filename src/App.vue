<template>
  <div id="app">
    <div id="title_div">
      <img src="./img/giphy.jpg" alt="">
      <h1 id="title">Giphy Search</h1>
    </div>
    <input type="text" v-model="search_input" v-on:keyup.enter="submit" placeholder="Enter search here...">
    <SearchResults v-bind:images="images"/>
  </div>
</template>

<script>
import SearchResults from './components/searchResults'


export default {
  name: 'app',
  components: {
    SearchResults
  },
   
  data: function() {
    return {
      search_input: "",
      images: "",
    }
  },
  methods: {
    submit: function() {
     axios.get('http://api.giphy.com/v1/gifs/search', {
       params: {
        q: this.search_input,
        api_key: 'Dx8iq7jDmztjj8JB95Y4TwfOU6lvM19P',
        limit: 36
       }
     })
      .then(response => { this.images = _.chunk(response.data.data, 9)});
      this.search_input = "";
    }
  }
}
</script>

<style>
body {
  margin:0px;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#title_div {
  background: #000;
  color: #fff;
  font-size: 2em;
  padding-top:1em;
  margin:0px;
  display: grid;
  grid-template-columns: auto;
  align-content: center;
  justify-content: center;
}
#title {
  
}
#title_div img {
  height:3em;
  width: auto;
  justify-self: center;
}
input {
  margin-top: 2em;
  padding:.5em;
  width:90%;
  max-width: 900px;
  font-size:2em;
}
</style>
