<template>
     <div class="header-container"> 

        <img src="../assets/Netflix-logo.png" alt="">
        
        <div class="nav-menu">
            <div><a href="#">Home</a></div>
            <div><a href="#">Serie Tv</a></div>
            <div><a href="#">Film</a></div>
            <div><a href="#">Originali</a></div>
            <div><a href="#">Aggiunti di recente</a></div>  
            <div><a href="#">La mia lista</a></div>
        </div>

        <div class="info-container">
            <button @click="$emit('search', searchString)">Cerca</button>
            <input @keyup.enter="$emit('search', searchString)" type="text" v-model="searchString">
            <div>Bambini</div>
            <div>Notifiche</div>
            <div>Profilo</div>
        </div>

    </div>
</template>

<script>

export default {
    name: 'Header',
    data() {
        return {
            searchString: '',
        }
    }, 

}
</script>

<style lang="scss" scoped>

.header-container {
    display: flex;
    align-items: center;
    font-size: 18px;
    padding: 12px 24px;
    background-color: black;
    img {
        width: 200px;
    }
    .nav-menu {
        display: flex;
        flex-grow: 1;
        * {
            margin-left: 12px;
            color: gray;
            text-decoration: none;
            &:hover {
                color: white ;
            }                
        }
    }
    .info-container {
        display: flex;
        button{
            color: black;
            width: 70px;
            border-radius: 25px;
        }
        
        input{
        background-color: #303030;
        border: 2px white solid;
        }
        input::placeholder{
        color: grey;
        }
        * {
            margin-left: 12px;
            color: white;
            cursor: pointer;
        }
    }
}

</style>