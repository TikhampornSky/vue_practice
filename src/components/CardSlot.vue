<template>
  <li> 
    <img src="https://cdn-icons-png.flaticon.com/512/3135/3135715.png" />
    <hr/>
    <slot name="card-header"></slot>           <!-- เนื้อหาที่ต้องการแทรกเข้าไป ที่ต้องการให้มีความแตกต่างกันได้ -->
    <slot name="card-button"></slot>
    <slot name="card-content"></slot>
  </li>
</template>

<script>
export default {

}
</script>

<style scoped>
    li{
        margin: 1rem 0;
        font-size: 1.25rem;
        font-weight: bold;
        background: rgb(1, 248, 59);
        padding: 0.5rem;
        color:black;
        border-radius: 25px;
    }
    img{
      width: 100px;
      height: 100px;
    }
</style>