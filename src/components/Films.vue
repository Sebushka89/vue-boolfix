<template>
   <div class="film-container">
        <div class="film-content">
            <img src="https://image.tmdb.org/t/p/w342/hQq8xZe5uLjFzSBt4LanNP7SQjl.jpg" alt="">
            
            <div class="info">
                <h4>{{title}}</h4>
                <div> Titolo Originale: {{original_title }}</div>
                <div>Lingua: {{original_language }}</div>
                <div>Voto: {{vote_average }}</div>   
            </div>  
        </div>
    </div>
</template>

<script>
export default {
    name: 'Films' ,
    props:{
        title: String,
        original_title: String,
        original_language: String,
        vote_average: String,
    }

}
</script>

<style lang="scss" scoped>

.film-content {
    height:500px;
    width: 300px;
    position: relative;
    margin: 0 20px;

    &:hover .info{
        display: block;
    }
    &:hover img{
        opacity: 0.5;
    }
    img {
        width: 100%;
        height: 100%;
        cursor: pointer;
        opacity: 1;
    }
    .info {
        position: absolute;
        text-align: center;
        top:50%;
        left: 50%;
        transform: translate(-50%,-50%);
        display: none;
        cursor: pointer;
        width: 100%;
    }
}
</style>