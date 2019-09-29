<template>
    <div>
        <ul class="fruitUl">
           <li class="fruit" v-for="fruit in fruitsData" :key="fruit">{{fruit}}</li>
        </ul>
        <ul class="imgUl">
            <li class="test-img"><img :src="imgData[0]" alt=""></li>
        </ul>
        <div>
            <a href="#">给混合器传递参数</a>
            <h3>我是谁，我从哪里来，我要到哪里去</h3>
        </div>
        <div class="div-test">
            <span>同志们</span>
        </div>
        
    </div>
</template>
<script>
export default {
    data(){
        return {
          imgData:[require('../assets/horse.jpg')],
          fruitsData:['苹果','香蕉','雪梨','葡萄']
        }
    }
}
</script>
<style lang="scss" scoped>
    @import '../assets/scss/test.scss';
</style>