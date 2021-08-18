<template>
    <div>
        <Header />
        <h1>Add Restaurant Details</h1>
        <form class="add">
            <img class="img-responsive" src="../assets/b_logo.png" alt="The Foodies Hub"> 
            <input type="text" v-model="restaurant.restname"  name="restname" placeholder="Enter Restaurant Name" /><br>
            <input type="text" v-model="restaurant.address" name="address" placeholder="Enter Address" /> <br>
            <input type="text" v-model="restaurant.contact" name="contact" placeholder="Enter Contact" /> <br>
            <button type="button" v-on:click="addRest">Add New Restaurant</button>
        </form>
    </div>
</template>

<script>
import axios from "axios";
import Header from './Header.vue';
export default {
    name:"Add",
    components:{
        Header
    },
    data(){
        return{
            restaurant:{
                restname:"",
                address:"",
                contact:"",
            }
        }
    },
    methods:{
        async addRest(){
            const addRestData= await axios.post("http://localhost:3000/restaurants",{
                    name:this.restaurant.restname,
                    address:this.restaurant.address,
                    contact:this.restaurant.contact,
            });
            if(addRestData){
                this.$router.push({name:"Home"});
            }
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