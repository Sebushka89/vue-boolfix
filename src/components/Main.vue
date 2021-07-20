<template>
    <main class="py-3">
        <div class="container-main">
            <div class="films">
                <h1 v-if="films.length != 0" class="text">FILM</h1>
                <div class="d-flex">
                    <Films v-for="film in films" :key="film.id" :content="film"/>
                </div>
            </div>
            <div class="series">
                <h1 v-if="series.length != 0" class="text">SERIE TV</h1>
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
    color: rgb(255, 09, 20);
  }
  .films{
    overflow-x: hidden;
  }
  .series{
      overflow-x: hidden;
  }
}


</style>