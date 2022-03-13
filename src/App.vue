<template>
  <div id="nav">
    <Navbar/>
  </div>
  <router-view/>
   <Footer/>
</template>
<script>
import Navbar from "@/components/Navbar.vue"
import Footer from "@/components/Footer.vue"
export default {
  components:{
    Navbar,
    Footer
  }
  
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  height: 100vh;
  background:linear-gradient(135deg, #8f0583, #c015cf, #ff00ea);
  background-color:#184e8e;
  font-family:'Source Sans Pro', sans-serif;
}
@media (min-width:400px) {
  #app{
    height:100vh;
  }
}
#nav a {
  font-weight: bold;
  color: #2c3e50;
}
#nav{
  padding: 30px;
}
#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
