<template>
  <div>
    <!-- <h1>{{message}}</h1> -->
    <!-- <PersonData name="Jane" salary=30000 /> -->      <!-- Send props to child และ ถ้ามีหลายอัน ต้องมีช่องว่างก่อนถึง --> 
    <div>
        <ul>
            <PersonData 
                v-for="(item, index) in employees"
                :key="index"
                :id="500"
                :name="item.name"
                :salary="item.salary"
                :department="item.department"
                :gender="item.gender"
                :skill="item.skill"
                :isVisible=true
                @show="toggleVisible2"
                @delete="removeEmployee2"            
            />  
            <PersonData 
                v-for="(item, index) in employees_sample"
                :key="index"
                :id="item.id"
                :name="item.name"
                :salary="item.salary"
                :department="item.department"
                :gender="item.gender"
                :skill="item.skill"
                :isVisible="item.isVisible"
                @show="toggleVisible"
                @delete="removeEmployee"            
            />  <!-- @show คือ event show ที่ลูกส่งมา ซึ่งอันนี้เป็นข้อมูลตัวอย่าง -->
        </ul>
    </div>
  </div>
</template>

<script>

import PersonData from './PersonData.vue'

export default {
    name:"ListData",
    data(){
        return {
            message: "ข้อมูลพนักงาน",
            employees_sample:[                     //สมมติว่าคือข้อมูลที่ดึงได้จากฐานข้อมูล
                {id:1, name:"Tontan",salary:20000 ,department:"โปรแกรมเมอร์" ,isVisible:false, gender:"ชาย",skill:['ภาษาจีน','ภาษาญี่ปุ่น','ภาษาอังกฤษ']},
                {id:2, name:"Jim",salary:30000 ,department:"ฝ่ายการตลาด" ,isVisible:false, gender:"หญิง",skill:['ภาษาจีน','ภาษาอังกฤษ']},
                {id:3, name:"Jane",salary:27000 ,department:"กราฟฟิค" ,isVisible:false, gender:"ชาย",skill:['ภาษาญี่ปุ่น','ภาษาอังกฤษ']},
            ]
        }
    },
    components:{
        PersonData,
    },
    methods:{
        toggleVisible(id){
            console.log("child ID: " + id)
            this.employees_sample = this.employees_sample.map((item) => {
                if(item.id == id) {
                    return {...item, isVisible:!item.isVisible}         // ...item คือ ตัวอื่นๆเหมือนเดิม
                }
                return item
            })
        },

        removeEmployee(id){
            this.employees_sample = this.employees_sample.filter(item=>{           //กรอกเอาแค่เฉพาะอันที่ id ไม่เท่ากับตัวที่จะลบ
                return item.id != id
            })
        },

        //----------สำหรับข้อมูลที่มีการกรอกเข้าไป แต่จะมีปัญหาเนื่องจากค่า id ยังไม่ได้กำหนดถูกต้องตามที่ควร--------------
    },
    props:['employees']               //รับค่าจาก props จาก App.js ในกรณีถ้ามี
}
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    ul{
        list-style: none;
        margin: 1rem 0;
        padding: 0;
    }
</style>