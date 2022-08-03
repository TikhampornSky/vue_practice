<template>    <!-- สำหรับแสดงผล -->
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App 1234"/>      <!-- component -->
  <ListData />
  <EmployeeTest/>
</template>

<script>  
import HelloWorld from './components/HelloWorld.vue'
import EmployeeTest from './components/EmployeeTest.vue'
import ListData from './components/ListData.vue'

export default {
  name: 'App',
  components: {     
    HelloWorld,
    EmployeeTest,
    ListData
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
