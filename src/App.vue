<template>
  <!-- สำหรับแสดงผล -->
  <header>
    <h1>ระบบจัดการข้อมูลของพนักงาน</h1>
  </header>
  <FormComponent @save="insertEmployee" />
  <section class="employee-content" v-if="employees.length >= 0" >
    <!--
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App 1234"/>  -->
    <!-- component -->
    <!-- <ListData :employees="employees"/> -->
    <!-- props (ส่งให้ ListData) -->
    <h2>ข้อมูลพนักงาน</h2>
    <ListData :employees="employees" />
    <!-- <EmployeeTest/> -->
  </section>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
//import EmployeeTest from './components/EmployeeTest.vue'
import ListData from "./components/ListData.vue";
import FormComponent from './components/FormComponent.vue'

export default {
  name: "App",
  components: {
    //HelloWorld,
    //EmployeeTest,
    ListData,
    FormComponent,
  },
  data(){
    return{
      employees:[]
    }
  },
  methods:{
    insertEmployee(data){
      this.employees.push(data)           //push into the array
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}
body {
  margin: 0;
}
header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  background-color: purple;
  color: blanchedalmond;
  text-align: center;
}

.employee-content {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
}

.employee-content h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: purple;
  margin: 0 0 1rem 0;
}
/*
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
*/
</style>
