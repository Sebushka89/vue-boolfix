<template>
    <main class="py-3">
        <div class="container-main">
            <div class="films">
                <h1 v-if="films.length != 0" class="text">Film</h1>
                <div class="d-flex">
                    <Films v-for="film in films" :key="film.id" :content="film"/>
                </div>
            </div>
            <div class="series">
                <h1 v-if="series.length != 0" class="text">Serie TV</h1>
                <div class="d-flex">
                    <Films v-for="serie in series" :key="serie.id" :content="serie"/>
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
            
        }
    }, 

}
</script>

<style lang="scss" scoped>
main{
  background-color: #141414;
  padding-left: 24px;
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