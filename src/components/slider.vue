<template>
<div>
    <div>
       <h3>简单轮播图</h3>
       <el-carousel height="533px" arrow="never" :interval="3000">
           <el-carousel-item v-for="(item,index) in imgData" :key="index" trigger="click">
               <img :src="item" alt="">
           </el-carousel-item>
       </el-carousel>
    </div>
</div>
</template>
<script>
export default {
    data(){
        return {
          imgData:[require('../assets/deer.jpg'),require('../assets/fox.jpg'),require('../assets/horse.jpg'),require('../assets/horse_2.jpg'),require('../assets/lions.jpg'),require('../assets/monkey.jpg')]
        }
    }
}
</script>
<style scoped>
    .el-carousel{
        width:800px;
    }
</style>