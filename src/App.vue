<template>
  <div id="app">
    <Header />
    <Main :films="films" />
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
      films:[]
    }
  },
  created () {
    axios.get('https://api.themoviedb.org/3/search/movie?api_key=3af7b5148292f04866b6873f768ef9a8&query=ritorno+al+futuro').then((result)=>{
      this.films= result.data.results;
      console.log(this.films)  //controllare la lista se effettivamente fatto chiamata, devo cancellare dopo
    })
  }
}
</script>

<style lang="scss">
@import "./style/app.scss"

</style>
