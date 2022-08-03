<template>
  <div>
    <h1>{{message}}</h1>
    <PersonData name="Jane" salary=30000 />       <!-- Send props to child -->
    <PersonData name="JoJo" salary=20000 />
    <PersonData name="Jim" salary=80000 />        <!--ถ้ามีหลายอัน ต้องมีช่องว่างก่อนถึง /> -->
  </div>
</template>

<script>

import PersonData from './PersonData.vue'

export default {
    name:"ListData",
    data(){
        return {
            message: "ข้อมูลพนักงานที่มีอยู่เดิม"
        }
    },
    components:{
        PersonData
    }
}
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h1{
        background-color: rgb(117, 175, 117);
    }
</style>