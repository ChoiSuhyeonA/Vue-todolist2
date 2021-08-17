<template>
  <div id="app">
    <h1>
      {{ title }}
    </h1>
    <nav>
      <div class="link-group">
      <router-link to="/home" class="link">List</router-link>
        <router-link to="/item" class="link2">New</router-link>
      </div>
   
    </nav>
    <router-view></router-view>
  </div>
</template>

<script>


export default {
  name: 'App',
 data(){
   return {
     title: 'vue petlist'
   }
 }
}
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
 
}
.link-group{
  display: flex;
  justify-content:center;
}
.link{
  
  margin-right: 10px;
   color: rgb(0, 255, 157);
   text-decoration : none;
   background-color: rgb(216, 247, 221);
  font-size: 20px;
  padding : 0.5em;
  width: 300px;
 
}
.link2{
 
   width: 300px;
   color: rgb(161, 243, 67);
   text-decoration : none;
     background-color: rgb(216, 247, 221);
    font-size: 20px;  
    padding : 0.5em;
}
</style>
