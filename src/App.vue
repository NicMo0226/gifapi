<template>
  <GiphySearch msg="Search for your Favourite Gifs!!"/>
  <GiphyTrending msg="Trending Gifs"/>
    <GiphyFooter msg="Gifs from Giphy"/>
</template>

<script>
import GiphySearch from './components/GiphySearch.vue'
import GiphyTrending from './components/GiphyTrending.vue'
import GiphyFooter from './components/GiphyFooter.vue'

export default {
  name: 'App',
  components: {
    GiphySearch,
    GiphyTrending,
    GiphyFooter
      }
  }
 </script>

<style>
#app {
  font-family:'Courier New', Courier, monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 100%;
  overflow-x: hidden;
 }
</style>
