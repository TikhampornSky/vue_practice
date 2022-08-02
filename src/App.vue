<template>    <!-- สำหรับแสดงผล -->
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <section> Tontan's Project </section>
  <img :src="picture"  :width="size" :height="size"/>         <!-- ผูก Attribute (e.g src, width, height) กับตัว data โดยจะใส่ v-bind: หรือ : ก็ได้ -->
  <h1>ชื่อ-นามสกุลของฉัน: {{firstname}} {{lastname}}</h1>    <!-- เป็นการดึงเอาค่า proprty ชื่อ firstname มาแสดง -->
  <h1>ประวัติของคุณ: {{getFullname()}} </h1>
  <h2>ที่อยู่: <span v-html="address"></span></h2>
  <p>Social: <a :href="social" target="_blank">facebook</a></p>
  <p> งานอดิเรก </p>
  <ul>
    <li>{{hobby[0]}}</li>
    <li>{{hobby[1]}}</li>
    <li>{{hobby[2]}}</li>
  </ul>
  <p> ข้อมูลพื้นฐาน: </p>
  <ul>
    <li>เพศ: {{general.gender}}</li>
    <li>น้ำหนัก: {{general.weight}} Kg</li>
    <li>ส่วนสูง: {{general.height}} cm.</li>
    <li>เป็นโรคติดต่อหรือไม่: {{general.status}} </li>
  </ul>
</template>

<script>  
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data() {    //data จะส่งค่ากลับมาในรูปแบบ Object โดยค่าที่ส่งกลับมานั้นสามารถนำไปใช้ใน template หรือ ส่วนอื่นๆของ Component ได้
    return {
      firstname: "Tontan",
      lastname: "Tomato",
      age: 21,
      address: "<i>กรุงเทพมหานคร</i>",
      picture: "https://cdn-icons-png.flaticon.com/512/219/219986.png",
      size: 70,
      social: "https://www.facebook.com/",
      hobby: ["ฟังเพลง", "ดูหนัง", "นอน"],
      general: {gender: "หญิง", weight:47, height:163, status:false}
    }
  },
  methods:{
    getFullname() {
      return "Miss " + this.firstname + " " +this.lastname
      //return `${this.firstname}  ${this.lastname}`
    }
  },
  components: {
    HelloWorld
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
