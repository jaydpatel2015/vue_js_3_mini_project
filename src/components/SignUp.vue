<template>
    <div class="signUpBox">
        <img class="img-responsive" src="../assets/b_logo.png" alt="The Foodies Hub" srcset="">
        <h1>New User Sign Up</h1>
        <div class="register">
            <input type="text" v-model="name" placeholder="Enter Username"/> <br>
            <input type="email" v-model="email" placeholder="Enter Email" /> <br>
            <input type="password" v-model="password" placeholder="Enter Password" /> <br>
            <button v-on:click="signUp" class="">Sign up</button>&nbsp;
            <button><router-link to="/login">Login</router-link></button>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    Name:"SignUp",
    data(){
        return{
            name:"",
            email:"",
            password:""
        }
    },
    methods:{
        async signUp(){
                let res=await axios.post("http://localhost:3000/user",{
                    email:this.email,
                    name:this.name,
                    password:this.password
                });
                console.warn (res);
                if(res.status == 201){
                    this.$router.push({name:"Home"});
                    localStorage.setItem("signed-up users",JSON.stringify(res.data));
                }
        }
    },
    mounted() {
        let user=localStorage.getItem("user-info");
        if(user){
            this.$router.push({name:"Home"});
        }
    }
}
</script>

<style scoped>
    h1{
        color: #fd8700;
    }
</style>
