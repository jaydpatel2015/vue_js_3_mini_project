<template>
    <div>
        <Header />
        <h1>Hello {{name}},Welcome to The Foodies Hub</h1>
    </div>
    <h2> Restaurant Lists </h2>
    <div class="div-table">
        <table class="table">
            <thead class="table-head">
                <tr>
                    <th>Rest. ID</th>
                    <th>Restaurant Name</th>
                    <th>Address</th>
                    <th>Contact</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody v-for="item in restaurantName" :key="item" class="table-body">
                <tr>
                    <td>{{item.id}}</td>
                    <td>{{item.name}}</td>
                    <td>{{item.address}}</td>
                    <td>{{item.contact}}</td>
                    <td><button><router-link :to="'/update/'+item.id">Update</router-link></button>
                    <button v-on:click="delRest(item.id)">Delete</button></td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import axios from 'axios'
import Header from './Header.vue'
export default {
    name:"Home",
    components:{
        Header
    },
    data(){
        return{
            name:"",
            restaurantName:[]
        }
    },
    methods:{
        async delRest(id){
            const delRestData=await axios.delete("http://localhost:3000/restaurants/"+id)
            if(delRestData){
                this.refreshPage()      
            }
        },
        async refreshPage(){
            let uName=localStorage.getItem('login-info')
            this.name=JSON.parse(uName).name
            if(!uName){
                this.$router.push({name:"SignUp"})
            }
            const rname= await axios.get("http://localhost:3000/restaurants");
            this.restaurantName=rname.data;        
        }
    },
    mounted(){
        this.refreshPage();
    }
}

</script>

<style scoped>
    h1{
        color:#fd8700;
    }
    h2{
        color:red
    }
</style>