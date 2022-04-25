<template>
  <div id="search-main">
    <h1>{{ msg }}</h1>
    <div id="search-container">
      <input class="searchbox" name="search" v-model="searchTerm">
      <!--search input field. v-model directive binds search variable to searchTerm-->
      <button id="search-btn" @click="getGifs"><img src="https://icons.nic-edesign.com/search-grey.png"></button>
    </div><br><br>
    <h3 id="title-2">Or select from the most popular Gif Categories</h3>
    <input type="radio" class="radios" v-model="searchTerm" value="reactions"> <!--categories-->
    <label>Reactions</label>
    <input type="radio" class="radios"  v-model="searchTerm" value="entertainment">
    <label>Entertainment</label>
    <input type="radio" class="radios" v-model="searchTerm" value="artists">
    <label>Artists</label>
     <input type="radio" class="radios" v-model="searchTerm" value="sports">
    <label>Sports</label>
    <input type="radio" class="radios" v-model="searchTerm" value="stickers">
    <label>Stickers</label><br>
    <button id="cat-btn" @click="getGifs"><!--using search button to search the category term - temp fix-->
      Get GIFs</button>
      <div id="main">
      <ul class="gif-container">
        <li><img class="gif-clip" v-for="gif in gifs" :src="gif" :key="gif.id"></li>
        <!--gif images with key binding-->
      </ul>
    </div>
  </div>
</template>

<script>
  
  export default {
    name: 'GiphySearch', // to import to vue
    props: {
          msg: String
    },
    data() {
      return {
        searchTerm: "",
        gifs: []//return gifs
      };
    },
    methods: {
      getGifs() {
        let apiKey = "ZNZqTgRX91nq24EL1MquGLCsZisPDx2j"; //giphy api key
        let searchEndPoint = "https://api.giphy.com/v1/gifs/search?"; //giphy search endpoint
        let limit = 24; //return limit
        let url = `${searchEndPoint}&api_key=${apiKey}&q=${
        this.searchTerm}&limit=${limit}`; //search url

        fetch(url)
          .then(response => {
            return response.json(); //returns the respnse in json
          })
          .then(json => {
            this.buildGifs(json); //build url query
          })
          .catch(err => {
            console.log(err);
          })
      },
      buildGifs(json) {
        this.gifs = json.data.map(gif => gif.id).map(gifId => {
          return `https://media.giphy.com/media/${gifId}/200.gif`; //map the gif id to the query
        });
      }
    }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/*  categories */
.radios{
  margin-left: 2em;
  margin-top: 18px;
}
/*  category labels */
label {
  margin-left: 6px;
  font-size: 18px;
}
h3 {
  margin: 40px 0 0;
}
/* gif container  */
.gif-clip{
  padding-left: 4px ;
  padding-right: 4px;
  padding-top:4px;
  padding-bottom:4px;
  box-shadow: 0px 3px 5px rgba(0, 0, 0, 0.2);
}
ul {
  list-style-type: none;
  padding: 0;
}
h2 {
  line-height: 1.4em;
}
li {
  display: inline-block;
  margin: 20px 20px;
}
a {
  color: #42b983;
}
/* image - search icon   */
#search-icon{
  height:82%;
  width: 90%; 
  padding-top: 4px;
  padding-bottom: 4px;
  
}
/* container for input and button   */
#search-container {
  height: 3em;
  border-radius: 8px;
  background-color: white !important;
  box-shadow: 0px 3px 15px rgba(0, 0, 0, 0.2);
  width: 45%;
  margin: 0 auto;
  }
  /* input - search  */
.searchbox {
  height: 1em;
  position: relative;
  bottom:5px;
  width: 90%;
  border:1px solid white;
}
/* category - get gifs button  */
#cat-btn {
  border:1px solid white;
  background-color: white !important;
  border-radius: 8px;
  box-shadow: 0px 3px 10px rgba(0, 0, 0, 0.2);
  position: relative;
  font-family:'Courier New', Courier, monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 16px;
  margin-left: 10px; 
  height: 2em;
  width: 7em;
  font-weight: bold;
  color: #5429ff;
  padding-top: 3px;
  margin-top: 1em;
}
/* get gifs - hover - change color  */
#cat-btn:hover {
  background-color: #5429ff !important;
  color: white;
}
/*  search button */
#search-btn {
  top: 2px;
  height: 90%;
  border:1px solid white;
  background-color: white ;
  position: relative;
}
/*  search text */
input.searchbox {
  color: #2c3e50;
  font-size: 22px;
  padding: 7px;
}
/* search section div */
#search-main{
  background-color: #d5ffff;
  width: 100%;
  margin-bottom: 0;
  padding-top: 1em;
}
/*  main ssection div */
#main {
  padding-left: 2em;
  padding-right: 2em;
}
#title-2 {
  padding-bottom: 1em;
}
</style>