<template>
  <div id="app">
    <Header @search="searchSomething" />
    <Main :films="filteredFilms" />
  </div>
    
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Header,
    Main
  
  },
  data() {
    return {
      films:[],
      inputSearch:[],
    }
  },
  created () {
    axios.get('https://api.themoviedb.org/3/search/movie?api_key=3af7b5148292f04866b6873f768ef9a8&query=ritorno+al+futuro').then((result)=>{
      this.films= result.data.results;
      this.searchSomething('');
    })
  },
  computed:{
    filteredFilms(){
      if (this.inputSearch.length === 0){
        return this.films
      }

      return this.films.filter((element)=> {
        return element.title.toLowerCase().includes(this.inputSearch.toLowerCase()) 
      })
    }
  },
  methods: {
    searchSomething(searchString) {
      this.inputSearch = searchString.trim()
    }, 
  }
}
</script>

<style lang="scss">
@import "./style/app.scss"

</style>
