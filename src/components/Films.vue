<template>
  <div class=" my-4 px-1">
    <div class="card">
      <img :src="getImgPath()" alt="" class="card-img-top position-relative">
      <div class="card-body position-absolute">
        <div class="title">{{ content.title || content.name }}</div>
        <div class="subtitle" v-if="content.original_title != content.title || content.original_name != content.name">{{ content.original_title || content.original_name }}</div>
        <div class="language mt-2 mb-2">
          Lingua originale:
          <img :src="getFlagURL()" class="language-flag" :alt="content.original_language">
        </div>
        <div class="d-flex">
          <i v-for="star in 5" :key="star" class="fa-star" :class="fullStar(star)"></i> 
        </div>
        <div class="overview" v-if="content.overview">{{content.overview}}</div>
        <div class="overview" v-else>Informazioni non disponibili</div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Films',
  components:{
   
  },
  props: {
    content: Object
  },
  data() {
    return {
      flagURL:'',
    }
  },
  computed: {
    stars() {
      return Math.ceil(this.content.vote_average / 2)
    }
  },
  methods: {
    getFlagURL(){
      if (this.content.original_language == 'en') {
        return this.flagURL=require('@/assets/en.png')
        }else if(this.content.original_language == 'ko') {
        return this.flagURL=require('@/assets/ko.png')
        }
        else if(this.content.original_language == 'ja') {
        return this.flagURL=require('@/assets/ja.png')
        }else if(this.content.original_language == 'te' ||this.content.original_language == 'hi' ) {
        return this.flagURL=require('@/assets/te.png')
        } else{
        return this.flagURL='https://www.countryflags.io/' + this.content.original_language + '/shiny/64.png'
      }
    },
    getImgPath(){
      return (this.content.poster_path ? 'https://image.tmdb.org/t/p/w500' + this.content.poster_path : require('@/assets/notavailable.jpg'))
    },
    fullStar(star) {
      if (star < this.stars) {
        return 'fas'
        } else {
        return 'far'
        }
      }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.card{
  border: none;
  cursor: pointer;
  width: 275px;
}
.card:hover .card-body{
  display: block;
}
.card-img-top{
  filter: brightness(1);
  height: 380px;
}
.card:hover  {
  transform: scale(1.2);
  transform-origin: left;
  z-index: 1002;
  transition: all 0.5s ease-out;
}
.card:hover .card-img-top{
  filter: brightness(0.5)	;
}
.card-body{
  height: 100%;
  display: none;
  overflow: auto;
  color: white;
  font-size: 14px;
}
.card-body::-webkit-scrollbar {
  display: none;
}
.title{
  font-size: 20px;
  text-transform:uppercase ;
}
.subtitle{
    font-style: italic;
}
.language-flag{
  width: 20%;
}
.fa-star{
  color: 	rgb(255,215,0);
}
.overview{
  font-size: 12px;
  margin-top: 6px;
}

</style>