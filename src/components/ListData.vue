<template>
  <div>
    <!-- <h1>{{message}}</h1> -->
    <!-- <PersonData name="Jane" salary=30000 /> -->      <!-- Send props to child และ ถ้ามีหลายอัน ต้องมีช่องว่างก่อนถึง --> 
    <div>
        <ul>
            <PersonData 
                v-for="(item, index) in employees"
                :key="index"
                :id="item.id"
                :name="item.name"
                :salary="item.salary"
                :department="item.department"
                :isVisible="item.isVisible"
                @show="toggleVisible"
                @delete="removeEmployee"            
            />  <!-- @show คือ event show ที่ลูกส่งมา -->
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
            employees:[                     //สมมติว่าคือข้อมูลที่ดึงได้จากฐานข้อมูล
                {id:1, name:"Tontan",salary:20000 ,department:"โปรแกรมเมอร์" ,isVisible:false},
                {id:2, name:"Jim",salary:30000 ,department:"ฝ่ายการตลาด" ,isVisible:false},
                {id:3, name:"Jane",salary:27000 ,department:"กราฟฟิค" ,isVisible:false},
                {id:4, name:"John",salary:50000 ,department:"ฝ่ายขาย" ,isVisible:false},
                {id:5, name:"Fah",salary:80000 ,department:"ผู้ลงทุน" ,isVisible:false},
                {id:6, name:"Tonyod",department:"ผู้จัดการฝ่าย A",isVisible:false},
            ]
        }
    },
    components:{
        PersonData
    },
    methods:{
        toggleVisible(id){
            //console.log("child ID: " + id)
            this.employees = this.employees.map((item) => {
                if(item.id == id) {
                    return {...item, isVisible:!item.isVisible}         // ...item คือ ตัวอื่นๆเหมือนเดิม
                }
                return item
            })
        },

        removeEmployee(id){
            this.employees = this.employees.filter(item=>{           //กรอกเอาแค่เฉพาะอันที่ id ไม่เท่ากับตัวที่จะลบ
                return item.id != id
            })
        }
    }
    //props:['employees']               //รับค่าจาก props จาก App.js ในกรณีถ้ามี
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