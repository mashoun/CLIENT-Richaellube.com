<template>
<latestnews></latestnews>


</template>




<script>
  
import latestnews from '@/components/latestnews.vue'
// @yamama="dosomething()" 8alat
// @yamama="dosomething" sa7 iza bedak te5od el value of the emit
//import test from '@/components/test.vue'
  export default{
    data(){
      return {
        title:'Richaellube.com'
      }
    },
    methods:{
    },
    components:{
      latestnews
      //test
     
    }
  }
</script>

<style>
*{
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
