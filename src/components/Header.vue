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
            <div @click="$emit('search', searchString)" class="find">
                <i class="fas fa-search"></i>
            </div>
            <input @keyup.enter="$emit('search', searchString)" type="text" v-model="searchString" placeholder="Cerca..." autofocus>
            <div>BAMBINI</div>
            <div class="notifiche">
                <div class="dot-red"></div>
                <i class="fas fa-bell"></i>
            </div>
        </div>
        <img class="profile" src="../assets/p.png" alt="">
        <i class="fas fa-caret-down"></i>

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
    padding-right: 24px;
    background-color: black;
    img {
        width: 200px;
    }
    .nav-menu {
        display: flex;
        flex-grow: 1;
        text-align: center;
        * {
            margin-left: 12px;
            color: gray;
            text-decoration: none;
            &:hover {
                color: white ;
                transition: 0.3s;
            }                
        }
    }
    .info-container {
        display: flex;
        text-align: center;
        margin-right: 12px;
        align-items: center;
        color: white;
        .fa-search{
         font-size: 20px;
        }
        input{
        border: 2px white solid;
        border-radius: 15px;
        padding-left: 12px;
        }
        input::placeholder{
        color: lightgrey;
        }
        input:focus {
            outline:none!important;
        }
        * {
            margin-left: 12px;
            cursor: pointer;
        }
        .fa-bell{
            font-size: 20px;
            margin-left: 0;
        }
        .notifiche{
            position: relative;
            .dot-red{
                width: 11px;
                height: 11px;
                background-color: red;
                border-radius: 50%;
                position: absolute;
                top: 0;
                right: 0;
                
            }
        }
    }
    .profile{
        height: 70px;
        width: 70px;
        cursor: pointer;
    }
    .fa-caret-down{
        margin-left: 6px;
        color: white;
        cursor: pointer;
        font-size: 20px;        
    }
}

</style>