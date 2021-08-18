<template>
      <router-view></router-view>
</template>

<script>
export default {
  name: 'App',
  components: {
  }
}
</script>

<style>
body{
        margin: auto;
        padding: auto;
}
#app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
}
.nav{
        display: flex;
}
.nav li{
        list-style-type: none;
}
.img-responsive{
        height: 200px;
        width: 200px;
  }
.signUpBox, .loginBox, .add,.updateForm{
        margin-left: 40%;
        padding: 10px;
        border: 1px solid black;
        width: 300px;
        border: 1px solid black;
        border-radius: 10px;
        box-shadow: 0px 1px 5px rgba(0,0,0,0.7);
  }
.register input, .login input, .add input,.updateForm input{
        padding: 10px;
        margin-bottom: 15px;
        width: 200px;
        border: 1px solid black;
        border-radius: 10px;
        box-shadow: 0px 1px 5px rgba(0,0,0,0.7);
}
.register button, .login button, .add button,.updateForm button{
        padding: 15px;
        margin-bottom: 10px;
        border: 1px solid black;
        border-radius: 10px;
        box-shadow: 0px 1px 5px rgba(0,0,0,0.7);
        font-family: 'Calibri',sans-serif;
        font-size: 18px;
        cursor: pointer;
        font-weight: 600;
        background-color:rgb(0, 140, 255) ;
        color: white;
}
.register button a, .login button a{
        color: white;
        text-decoration: none;
}
.div-table {
        text-align: center;
        display: flex;
        justify-content: center;
}

.table .table-head tr th{
        border:1px solid black;
        padding: 10px;
        font-size: 18px;
        font-weight: 600;
}
.table .table-body tr td{
        border:1px solid black;
        padding: 10px;
        font-size: 18px;
}
</style>
