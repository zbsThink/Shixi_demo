<template>
    <div>
          <div @mouseover="sliderStatus = true" style="height:180px;width:615px;background:#f00;"></div>
          <el-row style="width:615px;">
              <el-col :span="4.5">
                <div class="left-nav">
                    <div v-for="(da,index) in navData" :key="index" @mouseover="nav = da.status;sliderStatus = false">
                        <el-col  :class="['nav',{isHover:nav === da.status}]">{{da.title}}<el-icon class="el-icon-arrow-right"></el-icon></el-col>
                    </div>
               </div>
              </el-col>
              <el-col :span="10" class="slider" v-if="sliderStatus" >
                  我是轮播图
              </el-col>
              <el-col :span="10" v-else>
                  <div class="nav-content" v-for="(da,index) in navData" :key="index">
                      <div v-for="(item,index) in da.Blist" :key="index">
                            <div style="margin-bottom:10px;" v-if="nav === da.status">
                                <span  class="sp1" style="color:#666;line-height:15px;">{{item.type}}<el-icon class="el-icon-arrow-right"></el-icon></span>
                                <span  v-for="(li,index) in item.list"  :key="index">
                                    <span class="sp2" @mouseout="removeHover"  @mouseover="addHover">{{li}}</span>
                                </span>
                            </div>
                      </div>
                  </div>
              </el-col>
              <!-- <el-col :span="10">wosh</el-col> -->
          </el-row>

    </div>
</template>
<script>
export default {
    data(){
        return {
           nav:'',
           sliderStatus:true,
           sp2:true,
           navData:[
               {
                   status:'ph',
                   title:'手机、电脑、数码',
                   Blist:[{
                     type:'手机配件',
                     list:['手机耳机','手机充电器','手机数据线']
                   },{
                     type:'数码配件',
                     list:['移动电源','苹果保护套/保护壳']
                   }
                   ]
               },
                {
                   status:'cp',
                   title:'电脑、办公',
                   Blist:[{
                     type:'设备/网络',
                     list:['路由器','随身wifi']
                   }]
               },
               {
                   status:'fs',
                   title:'服饰配件',
                   Blist:[{
                     type:'智能手环',
                     list:['智能手环']
                   }]
               }

           ]
        }
    },
    created(){
        console.log(this.nav)
        // console.log(this.spStatus)
    },
    mounted(){
    //    console.log(this.spStatus)
    },
    methods:{
        test(){
            console.log('我生效了')
            console.log(data)
        },
        addHover(event){
           event.currentTarget.className = 'spisHover'
        },
        removeHover(event){
           event.currentTarget.className = 'sp2'
        }
    }
}
</script>
<style scoped>
   .left-nav{
       width:210px;
       height:493px;
       background-color: #c91622;
       position:relative;
   }
   .left-nav .nav{
       /* margin-bottom:10px; */
       color:#fff;
       padding:4px 0;
       font:14px Microsoft Yahei, Hiragino Sans GB, Arial, sans-serif;
   }
   .left-nav .isHover{
       background:#fff;
       color:#c91622;
       padding:4px 0;
       border-left:1px solid #c91622;
       border-right:1px solid #c91622;
   }
   .left-nav .nav .el-icon-arrow-right{
       position:absolute;
       right:0;
       padding-right:10px;
   }
   .nav-content{
       color:#fff;
       font:12px Microsoft Yahei, Hiragino Sans GB, Arial, sans-serif;
   }
   .nav-content .sp1{
       color:#666;
       line-height:15px;
       font-size:12px;
       font-weight:bold;
   }
   .nav-content .sp2,.spisHover{
       border-left: 1px solid #CCC;
       color: #737373;
       padding: 0 8px;
       margin: 4px 0;
   }
   .nav-content .spisHover{
       color:#f00;
   }
   div.slider{
       border:1px solid #f00;
       height:493px;
       width:400px;
   }
   
</style>