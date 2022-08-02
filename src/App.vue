<template>    <!-- สำหรับแสดงผล -->
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <section> Tontan's Project </section>
  <img :src="picture"  :width="size" :height="size" ref="imageURL"/><br>         <!-- ผูก Attribute (e.g src, width, height) กับตัว data โดยจะใส่ v-bind: หรือ : ก็ได้ -->
                                                                                 <!-- ref จะคล้ายๆกับการตั้งชื่อ id หรือ class ใน tage HTML -->
  ระบุชื่อเล่น: <input type="text" v-on:input="setNickname"/>

  <form @submit="submitForm">  <!-- v-on:submit หรือ @submit ก็ได้  หากไม่ต้องการให้เกิดการรีเฟรช สามารถเขียนเป็น @submit.prevent ก็ได้ -->
    <label>กรุณาระบุความถนัดของท่าน: </label>
    <input type="text" ref="ableElement"/>
    <button type="submit"> submit</button>
  </form>

  <h1>ชื่อ-นามสกุลของฉัน: {{firstname}} {{lastname}}</h1>    <!-- เป็นการดึงเอาค่า proprty ชื่อ firstname มาแสดง -->
  <h1>ชื่อเล่น: {{nickname}} </h1>
  <h1>ความสามารถพิเศษ: {{ability}} </h1>
  <h1>อายุ: {{age}} </h1>
  <p>ประวัติของคุณ: {{getFullname()}} </p>
  <p>ที่อยู่: <span v-html="address"></span></p>
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
  <button @click="showData"> Click to see information </button>     <!-- You can use 'v-on:' or '@' -->
  <button @click="increase(10)"> Increase </button>            <!-- @click.ctrl คือ คลิกเมาส์ซ้าย + กดปุ่ม ctrl -->
  <button @click.middle="decrease"> Decrease</button>               <!-- @click.middle คือ คลิกเมาส์กลาง(scroll) แล้วถึงจะทำงาน -->
</template>

<script>  
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data() {    //data จะส่งค่ากลับมาในรูปแบบ Object โดยค่าที่ส่งกลับมานั้นสามารถนำไปใช้ใน template หรือ ส่วนอื่นๆของ Component ได้
    return {
      firstname: "Tontan",
      lastname: "Tomato",
      nickname:"",
      age: 21,
      address: "<i>กรุงเทพมหานคร</i>",
      ability:"",
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
    },

    showData(){
      alert(this.firstname)
    },

    increase(num){
      this.age += num
    },
    decrease(){
      this.age--
    },

    setNickname(event){
      this.nickname = event.target.value
    },

    submitForm(event){
      event.preventDefault()      //เพื่อให้ไม่เกิดการรีเฟรช หลังจากกดส่งแบบฟอร์ม
      //console.log(this.$refs.imageURL)    //ได้ผลลัพธ์เป็น tag เลย
      //console.log(this.$refs.ableElement)
      this.ability = this.$refs.ableElement.value
      alert("บันทึกแล้ว")
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
