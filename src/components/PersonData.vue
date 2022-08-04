<template>
    <CardSlot>
        <template v-slot:card-header>
            <h1>{{message}} {{name}}</h1>         <!-- show 'props' -->
        </template>

        <template v-slot:card-button>
        <button @click="showDescription(id)" ref="btnToggle">แสดงผลลัพธ์</button>&nbsp;
        <button @click="deleteEmployee(id)">ลบข้อมูล</button>
        </template>

        <template v-slot:card-content>
            <transition name="fade">
                <div v-show="isVisible">
                    <p> เงินเดือน: {{salary}}  ตำแหน่งงาน: {{department}} </p>
                </div>
            </transition>
        </template>
    </CardSlot>
</template>

<script>

import CardSlot from './CardSlot.vue'

export default {
    name:"PersonData",
    data(){
        return {
            message: "ชื่อพนักงาน: "
        }
    },
    //props:["name", "salary"]                  //รับค่า props ชื่อ name มาจาก parent (props =  parent --> child หรือที่เรียกว่า up to down)
    props:{
        id:{
            type:Number,
            require:true
        },
        name:{
            type:String,                        //กำหนดเงื่อนไข เพื่อตรวจสอบรูปแบบข้อมูลที่รับมาว่าต้องถูกต้อง โดยถ้าผิดจะแจ้งเป็น Warning
            require:true                        //ต้องมีการระบุค่า
        },
        salary:{
            type:Number,
            //require:true
            default:15000                       //กำหนดค่าเริ่มต้น
        },
        department:{
            type:String,
            require:true
        },
        isVisible:{
            type:Boolean
        }
    },
    methods:{
        showDescription(id) {
            //console.log(id)
            this.$refs.btnToggle.innerText = this.isVisible?'แสดงผลลัพธ์':'ซ่อนผลลัพธ์';
            this.$emit("show", id)      //ส่งสัญญาณไปหา parent โดยใช้คำสั่ง emit ซึ่งที่ส่งไปจะอยู่ในรูปแบบ event ชื่อว่า show
        },

        deleteEmployee(id){
            //console.log(id)
            this.$emit("delete", id) 
        }
    },

    components:{
        CardSlot
    }
}
</script>

<style scoped>
    li{
        margin: 1rem 0;
        font-size: 1.25rem;
        font-weight: bold;
        background: rgb(123, 234, 191);
        padding: 0.5rem;
        color:black;
        border-radius: 25px;
    }
    button{
        font:inherit;
        cursor: pointer;
        border: 1px solid rgb(5, 103, 18);
        background: rgb(1, 112, 88);
        color:white;
        padding: 0.05rem 1rem;
        box-shadow: 1px 1px 2px rgba(0,0,0, 0.26);
    }

    .fade-enter-from{
        opacity: 0;
    }
    .fade-enter-active{
        transition: all 0.5s linear;
    }
</style>