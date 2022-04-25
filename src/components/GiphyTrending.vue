<template>
  <div id="trending">
    <h1>{{ msg }}</h1>
    <ul class="gif-container">
    <li><img class="gif-clip" v-for="gif in gifs" :src="gif" :key="gif.id"></li>   <!--gif images with key binding-->
    </ul>
  </div>
</template>

<script>
export default {
  name: 'GiphyTrending',
  props: {
    msg: String
  },
  data(){
    return{
     gifs: [], //return gifs
    }
  },
  created() {
      this.getGifs();// new instance of get gifs
  },
  methods: {
    getGifs (){
      let apiKey = "1msQegdVLROjJf4LCqZCwP5l1lKt7nRS"; //giphy api key
      let trendingEndPoint = "https://api.giphy.com/v1/gifs/trending?"; //giphy trending endpoint
      let limit = 24; //return limit
      let url = `${trendingEndPoint}&api_key=${apiKey}&limit=${limit}`;//trending url
   
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
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
}
/* main section   */
#trending {
  padding-left: 2em;
  margin-top: 0;
  padding-right: 2em;
  padding-top: 1em;
  background-color: rgb(238, 238, 238);
}
/* gif container  */
.gif-clip{
  padding-left: 4px ;
  padding-right: 4px;
  padding-top:4px;
  padding-bottom:4px;
  box-shadow: 0px 3px 5px rgba(0, 0, 0, 0.2);
}
a {
  color: #42b983;
}
</style>
