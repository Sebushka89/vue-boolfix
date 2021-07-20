<template>
  <div id="app">
    <Header @search="searchContent" />
    <Main :films="films" :series="series" />
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
      series:[],
      apiFilmsURL: 'https://api.themoviedb.org/3/search/movie',
      apiSeriesURL:'https://api.themoviedb.org/3/search/tv',
      apiKey: '3af7b5148292f04866b6873f768ef9a8',
      language: 'it-IT',
      apiOpeningFilms:'https://api.themoviedb.org/3/movie/popular?api_key=3af7b5148292f04866b6873f768ef9a8&language=it-IT',
      apiOpeningTv:'https://api.themoviedb.org/3/tv/popular?api_key=3af7b5148292f04866b6873f768ef9a8&language=it-IT',
    }
  },
  created(){
    this.createApiFilms(this.apiOpeningFilms);
    this.createApiTv(this.apiOpeningTv)
  },
  methods:{
    searchContent(searchText){
      if(searchText.trim()==''){
        this.createApiFilms();
        this.createApiTv()
      }
      // RICERCA FILM
      axios.get(this.apiFilmsURL, {
        params:{
          api_key: this.apiKey,
          language: this.language,
          query: searchText
        }
      })
      .then( response =>{
        this.films = response.data.results;
      })
      // RICERCA SERIE TV
      axios.get(this.apiSeriesURL, {
        params:{
          api_key: this.apiKey,
          language: this.language,
          query: searchText
        }
      })
      .then( response =>{
        this.series = response.data.results;
      })
    },
    createApiFilms(){
      axios.get(this.apiOpeningFilms).then((response)=>{
      this.films = response.data.results;
      })    
    },
    createApiTv(){
      axios.get(this.apiOpeningTv).then((response)=>{
      this.series = response.data.results;
      })    
    },
  }
}
</script>

<style lang="scss">
@import "./style/app.scss"

</style>
