<template>
    <main class="py-3">
        <div class="container">
            <div class="films ">
                <h1 v-if="films.length != 0" class="text">FILM</h1>
                <div class="row row-cols-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-5">
                <Films v-for="film in films" :key="film.id" :content="film"/>
            </div>
        </div>
            <div class="series">
                <h1 v-if="series.length != 0" class="text">SERIE TV</h1>
                <div class="row row-cols-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-5">
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
  height: calc(100vh - 100px);
  background-color: #141414;
  .text{
      color: rgb(255, 09, 20);
  }
}


</style>