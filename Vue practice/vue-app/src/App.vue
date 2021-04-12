<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <div>{{num}}</div>
    <HelloWorld msg="Welcome to Your Vue.js App" v-bind:title='num'/>
    <div>
      <button v-on:click="testFunction">get Data</button>
    </div>  
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios'
//import ComponentsTest from './components/ComponentsTest.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data: function(){
    return{
      num: "100"
    }
  },
  methods: {
    testFunction: function(){
      var vm=this;
      axios.get('http://localhost:8000/vuetest')
      .then(function(response){
        console.log(response.data);
        vm.num=response.data;
      })
      .catch(function(error){
        console.log(error);
      });
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
</style>
