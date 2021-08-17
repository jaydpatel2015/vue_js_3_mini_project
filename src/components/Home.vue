<template>
    <div>
        <Header />
        <h1>Hello {{name}},Welcome to The Foodies Hub</h1>
    </div>
</template>

<script>
import Header from './Header.vue'
export default {
    name:"Home",
    components:{
        Header
    },
    data(){
        return{
            name:""
        }
    },
    mounted(){
        let uName=localStorage.getItem('login-info')
        this.name=JSON.parse(uName).name
        if(!uName){
            this.$router.push({name:"SignUp"})
        }
    }
}

</script>

<style scoped>
    h1{
        color:#fd8700;
    }
</style>