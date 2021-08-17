<template>
    <div class="loginBox">
        <img class="img-responsive" src="../assets/b_logo.png" alt="The Foodies Hub" srcset="">
        <h1>Login</h1>
        <div class="login">
            <input type="email" v-model="email" placeholder="Enter Email" /> <br>
            <input type="password" v-model="password" placeholder="Enter Password" /> <br>
            <button v-on:click="loginClicked">Login</button>&nbsp;
            <button><router-link to="/signup">Sign Up</router-link></button>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name:"Login",
    data(){
        return{
            email:"",
            password:""
        }
    },
    methods:{
        async loginClicked(){
            const res = await axios.get(`http://localhost:3000/user?email=${this.email}&password=${this.password}`);
            console.log(res)
            if(res.status == 200 && res.data.length > 0){
                localStorage.setItem("login-info",JSON.stringify(res.data[0]));
                this.$router.push({name:"Home"})
            }else{
                alert("login failed! kindly recheck email & password")    
            }
        }
    },
    mounted(){
        let user=localStorage.getItem("login-info");
        if(user){
            this.$router.push({name:"Home"});
        }
    },
}
</script>

<style scoped>
    h1{
        color:royalblue;
    }
</style>