<template>
    <main class="py-3">
        <div class="container-main">
            <h1 v-if="films.length != 0" class="text">Film</h1>
            <div class="films">
                <div class="d-flex justify-content-center">
                    <div class="button-left" @click="goBackFilms()"><i class="fas fa-chevron-left"></i></div>
                    <Films v-for="film in newArrayFilm" :key="film.id" :content="film"/>
                    <div class="button-right" @click="goForwardFilms()"><i class="fas fa-chevron-right"></i></div>
                </div>
            </div>
            <h1 v-if="series.length != 0" class="text">Serie Tv</h1>
            <div class="series">
                <div class="d-flex justify-content-center">
                    <div class="button-left" @click="goBackSeries()"><i class="fas fa-chevron-left"></i></div>
                    <Films v-for="serie in newArraySeries" :key="serie.id" :content="serie"/>
                    <div class="button-right" @click="goForwardSeries()"><i class="fas fa-chevron-right"></i></div>
                </div>
            </div>
        </div>

    </main>
    
</template>

<script>
import Films from './Films.vue';
export default {
    name: 'Main',
    components:{
        Films
    },
    props:{
        films:Array,
        series: Array
    },
    data() {
        return {
           currentIndexFilms: 0,
           currentIndexSeries: 0
        }
    },
    computed:{
        startFilm() {
        return this.films
        },
        startSeries() {  
        return this.series
        },
        newArrayFilm() {
        return this.startFilm.slice(this.currentIndexFilms, (this.currentIndexFilms + 6))
        },
        newArraySeries() {
        return this.startSeries.slice(this.currentIndexSeries, (this.currentIndexSeries + 6))
        }
    },
    methods: {
        goForwardFilms() {
        this.currentIndexFilms += 6
        },
        goForwardSeries() {
        this.currentIndexSeries += 6
        },
        goBackFilms() {
        this.currentIndexFilms -= 6
        },
        goBackSeries() {
        this.currentIndexSeries -= 6
        }
    } 

}
</script>

<style lang="scss" scoped>
main{
  background-color: #141414;
  padding-left: 24px;
  .button-left{
    display: flex;
    align-items: center;
    color: white;
  }
  .button-right{
    display: flex;
    align-items: center;
    color: white;
    &:hover{
    transform:scale(1.5) ;
    }
  }
  .text{
    color: white;
  }
  .films{
    overflow-x: auto;
    overflow-y: hidden ;
  }
  /*modifica scrollbar*/
    ::-webkit-scrollbar {
        height: 10px;
    }

    ::-webkit-scrollbar-track {
        border-radius: 10px;
        box-shadow: inset 0 0 5px lightslategray; 
    }
    
    ::-webkit-scrollbar-thumb {
        background: gray; 
        border-radius: 10px;
    }

    ::-webkit-scrollbar-thumb:hover {
        background: rgb(97, 96, 96); 
    }
    .series{
      overflow-x: auto;
      overflow-y: hidden;
    }
    ::-webkit-scrollbar {
        height: 10px;
    }

    ::-webkit-scrollbar-track {
        border-radius: 10px;
    }
    
    ::-webkit-scrollbar-thumb {
        background: gray; 
        border-radius: 10px;
    }

    ::-webkit-scrollbar-thumb:hover {
        background: rgb(97, 96, 96); 
    }
}


</style>