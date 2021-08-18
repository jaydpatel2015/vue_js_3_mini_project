<template>
    <div>  
        <Header />
        <h1>Update Restaurant Details</h1>
         <form class="updateForm">
            <img class="img-responsive" src="../assets/b_logo.png" alt="The Foodies Hub"> 
            <input type="text" v-model="restaurant.name" name="name" /><br>
            <input type="text" v-model="restaurant.address" name="address" /> <br>
            <input type="text" v-model="restaurant.contact" name="contact" /> <br>
            <button type="button" v-on:click="updateRest">Update Restaurant Details</button>
            </form>
    </div>
</template>

<script>
import axios from "axios";
import Header from './Header.vue'
export default {
    name:"Update",
    components:{
        Header
    },
    data(){
        return{
            restaurant:{
                name:"",
                address:"",
                contact:"",
            }
        }
    },
    methods:{
        async updateRest(){
            const updateData=await axios.put("http://localhost:3000/restaurants/"+this.$route.params.id,{
                name:this.restaurant.name,
                address:this.restaurant.address,
                contact:this.restaurant.contact,
            });
            if(updateData.status == 200 ){
                this.$router.push({name:"Home"})
            }
        }
    },
    async mounted(){
        let uName=localStorage.getItem('login-info')
        this.name=JSON.parse(uName).name
        if(!uName){
            this.$router.push({name:"SignUp"})
        }
        const getId=await axios.get("http://localhost:3000/restaurants/" +this.$route.params.id)
        this.restaurant=getId.data
    }
}
</script>