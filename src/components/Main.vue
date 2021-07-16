<template>
    <div class="container">
        <Films v-for="(film, index) in films" :key="index"
        :title="film.title"
        :original_title="film.original_title"
        :original_language="film.original_language"
        :genre="film.genre"
        :vote_average="film.vote_average" />
    </div>
</template>

<script>
import Films from './Films.vue';
export default {
    name: 'Main',
    components:{
        Films
    },
    props:{
        films:Array
    },
    data() {
        return {
            
        }
    }, 

}
</script>

<style lang="scss" scoped>
.container{
    background-color: black;
    color: white;
    height: 100vh;
    padding: 30px;
    display: flex;
}


</style>