<template>    <!-- สำหรับแสดงผล -->
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

  <h1>เงินเดือน: {{salary}} บาท</h1>
  <button @click="increaseSalary()"> Increase </button> <br>
  <h1>รายได้ต่อปี: {{getIncome}} บาท</h1>
  <h1>ตำแหน่งงาน: {{getDepartment}} </h1>

  <h2>สุ่ม1 (Method): {{getRandomByMethod()}} </h2>    <!-- ได้ต่างกัน รันของใครของมัน -->
  <h2>สุ่ม2 (Method): {{getRandomByMethod()}} </h2>
  <hr/>
  <h2>สุ่ม1 (Computed): {{getRandomByComputed}} </h2>  <!-- ได้เหมือนเดิม ตราบใดที่ค่าไม่เปลี่ยน -->
  <h2>สุ่ม2 (Computed): {{getRandomByComputed}} </h2> 

  <p>ประวัติของคุณ: {{getFullname()}} </p>
  <p>ประวัติของคุณ2: {{getFullname2}} </p>     <!-- เรียก computed  -->
  <p>{{isvisible}} </p>

  <button @click ="toggleVisible"> {{isvisible? "ซ่อนข้อมูล": "แสดงผลลัพธ์"}} Click...</button> <br>
  <article v-show="isvisible">
    <!-- v-show = จะถูก render เรียบร้อยแล้ว แค่มันไม่ได้แสดงผลออกมา แต่ v-if จะถูกแทรกลงไปภายหลังหากเงื่อนไขเป็นจริง -->
    <p>ที่อยู่: <span v-html="address"></span></p>
    <p>Social: <a :href="social" target="_blank">facebook</a></p>
    <p v-if="hobby.length === 0">ไม่มีงานอดิเรก</p>    <!-- กรณีที่ hobby เป็นลิสต์ว่างๆ -->
    <div v-else>
      <p> งานอดิเรก </p>
      <ul>
        <li v-for="(item,index) in hobby" :key="index">{{index}} - {{item}}</li>      <!-- Key ต้องไม่ซ้ำกัน!!!! -->
      </ul>
    </div>
    <p> ข้อมูลพื้นฐาน: </p>
    <ul>
      <li v-for="(item,key) in general" :key="key">{{key}} - {{item}}</li>
    </ul>
  </article>
  <button @click="showData"> Click to see information </button>     <!-- You can use 'v-on:' or '@' -->
  <button @click="increase(10)"> Increase </button>            <!-- @click.ctrl คือ คลิกเมาส์ซ้าย + กดปุ่ม ctrl -->
  <button @click.middle="decrease"> Decrease</button>               <!-- @click.middle คือ คลิกเมาส์กลาง(scroll) แล้วถึงจะทำงาน -->
</template>

<script>  

export default {
  name: 'EmployeeTest',
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
      hobby: ["กินข้าว", "ดูหนัง", "ฟังเพลง", "ดูทีวี", "นอนนน", "เลี้ยงแมว"],
      general: {gender: "หญิง", weight:47, height:163, status:false},
      isvisible:false,
      salary: 10000
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
    increaseSalary() {
      this.salary += 10000
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
    },

    toggleVisible(){
      this.isvisible = !this.isvisible
    },

    getRandomByMethod(){
      return Math.random()
    }
  },
  computed:{  //Getter method และจะมีการดักจับค่าเมื่อมีการเปลี่ยนแปลง (รีใหม่เมื่อค่าเปลี่ยน แต่ method รีใหม่เวลา component Re-render)  
    getFullname2() {
      return `${this.firstname}  ${this.lastname}`
    },

    getRandomByComputed(){
      return Math.random()
    },

    getIncome() {
      return this.salary*12
    },

    getDepartment() {
      return this.salary >= 35000 ? "Project Manager" : "Programmer"
    }
  },
  watch:{       //ติดตามการเปลี่ยนแปลงของ Data หรือ Properties นั้นๆ
    salary(value){
      if (value > 50000) {
        alert("เงินเดือนมากไปแร้ว")    //ถ้าค่าที่ติดตามเข้าเงื่อนไข จะทำสิ่งนี้
        setTimeout(() => {
          this.salary = 20000
        },2000)                     //ผ่านไป 2 ms ค่าจะถูกรีเซ็ทกลับมาเป็นเหมือนเดิม
      }
    }
  },
  components: {     

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
