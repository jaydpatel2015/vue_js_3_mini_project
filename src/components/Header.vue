<template>
    
    <div class="navMenu">
        <router-link to="/">Home</router-link>
        <router-link to="/add">Add Restaurant</router-link>
        <a v-on:click="logOut" href="#">Log Out</a>
    </div>
</template>
<script>
export default {
    name:"Header",
    methods:{
        logOut(){
            localStorage.clear();
            this.$router.push({name:"Login"})
        }
    }
}
</script>

<style scoped>
    h1{
        color:burlywood
    }
    .navMenu{
        background-color: lightgrey;
        overflow: hidden;
    }   
    .navMenu a{
        padding: 16px 14px;
        margin-top: 10px;
        float: left;
        font-weight: 600;
        font-size: 16px;
        text-decoration: none;
        cursor: pointer;
        color:black
    }
    .navMenu a:hover{
        color:#fd8700
    }
</style>