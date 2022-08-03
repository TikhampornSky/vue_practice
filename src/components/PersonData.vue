<template>
  <h1>{{message}} {{name}}</h1>         <!-- show 'props' -->
  <h1>เงินเดือน: {{salary}}</h1>
</template>

<script>
export default {
    name:"PersonData",
    data(){
        return {
            message: "ข้อมูลพนักงาน"
        }
    },
    props:["name", "salary"]                  //รับค่า props ชื่อ name มาจาก parent (props =  parent --> child หรือที่เรียกว่า up to down)
}
</script>

<style scoped>
    h1{
        background-color: rgb(197, 228, 197);
    }
</style>