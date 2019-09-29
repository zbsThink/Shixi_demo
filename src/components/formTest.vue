<template>
    <div>
        <!-- 初始form表单 -->
        <!-- <el-form ref="form" :model="form" label-width="80px">
            <el-form-item label="活动名称" style="width:540px;" required>
                <el-input v-model="form.name" placeholder="请输入活动名称"></el-input>
            </el-form-item>
            <el-form-item label="活动区域">
                <el-select v-model="form.region" placeholder="请选择活动区域">
                    <el-option value="Beijing" label="区域一"></el-option>
                    <el-option value="ShangHai" label="区域二"> </el-option>
                    <el-option value="GuangDong" label="区域三"></el-option>
                </el-select>
            </el-form-item>
            <el-form-item label="活动时间">
                    <el-date-picker type="date" v-model="form.date1" placeholder="请选择日期">
                    </el-date-picker>
                    <span>-</span>
                    <el-time-picker type="time" v-model="form.date2" placeholder="请选择时间">
                    </el-time-picker>
            </el-form-item>
            <el-form-item label="及时配送">
                <el-switch v-model="form.delivery"> 
                </el-switch>
            </el-form-item>
            <el-form-item label="活动性质">
                <el-checkbox-group v-model="form.type">
                    <el-checkbox label="美食/餐厅线上活动" name="type"></el-checkbox>
                    <el-checkbox label="地推活动" name="type"></el-checkbox>
                    <el-checkbox label="线下主题活动" name="type"></el-checkbox>
                    <el-checkbox label="单纯品牌曝光" name="type"></el-checkbox>
                </el-checkbox-group>
            </el-form-item>
            <el-form-item label="特殊资源">
                <el-radio-group v-model="form.resource">
                    <el-radio label="线上品牌商赞助"></el-radio>
                    <el-radio label="线下场地免费"></el-radio>
                </el-radio-group>
            </el-form-item>
            <el-form-item>
                    <el-button type="primary" @click="onSubmit">立即创建</el-button>
                    <el-button>取消</el-button>
            </el-form-item>
        </el-form> -->

        <!-- 有验证规则的form表单绑定在form这个整体上 -->
        <el-form :model="ruleForm" ref="ruleForm" :rules="rules" label-width="80px" status-icon>
            <el-form-item label="手机号" prop="phoneNumber">
                <el-input v-model="ruleForm.phoneNumber" placeholder="请输入手机号码">
                </el-input>
            </el-form-item>
            <el-form-item label="密码" prop="password">
                <el-input show-password type="password"  v-model="ruleForm.password" placeholder="请输入密码"></el-input>
            </el-form-item>
            <el-form-item label="确认密码" prop="checkpass">
                <el-input show-password type="password"  v-model="ruleForm.checkpass" placeholder="请再次输入密码"></el-input>
            </el-form-item>
            <el-form-item label="邮箱" prop="email">
                <el-input v-model="ruleForm.email" placeholder="请输入邮箱账号"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="login('ruleForm')">登录</el-button>
                <el-button @click="resetForm('ruleForm')">重置</el-button>
            </el-form-item>
        </el-form>
    </div>
</template>
<script>
export default {
    data(){
        var checkPhoneNumber = (rule,value,callback) => {
            if(!value){
                 callback(new Error('手机号不能为空'))
            }else{
                if(value.length === 11){
                    if(!/^1([38]\d|4[579]|5[0-3,5-9]|6[6]|7[0-8]|9[89])\d{8}$/.test(value)){
                    callback(new Error('请输入正确手机号'))
                 }else{
                   callback()
                 }
                }else{
                    callback(new Error('请输入11位手机号'))
                }
            }
            
        };
        var validatePass = (rule,value,callback) => {
            if(!value){
                callback(new Error('密码不能为空'))
                // /^(?![0-9]+$)(?![a-zA-Z]+$)(?![_@#$%^&*]+$)[0-9a-zA-Z_@#$%^&*]{8-16}$/
            }else if(!/^(?![0-9]+$)(?![a-zA-Z]+$)(?![`~!@#$%^&*()_\-+=<>?:"{}|,.\/;'\\[\]·~！@#￥%……&*（）——\-+={}|《》？：“”【】、；‘'，。、]+$)[0-9A-Za-z,`~!@#$%^&*()_\-+=<>?:"{}|,.\/;'\\[\]·~！@#￥%……&*（）——\-+={}|《》？：“”【】、；‘'，。、]{8,16}$/.test(value)){
                callback(new Error("密码格式错误"))
            }else{
                callback()
            }
        };
        var validateCheckPass = (rule,value,callback) => {
            if(!value){
                callback(new Error('请再次输入密码'))
            }else if(this.ruleForm.password !== value){
                callback(new Error('密码不一致'))
            }else{
                callback()
            }
        };
        return {
           form:{
               name:'',
               region:'',
               date1:'',
               date2:'',
               delivery:false,
               type:'',
               resource:''
           },
           ruleForm:{
              phoneNumber:'',
              password:'',
              checkpass:'',
              email:''

           },
           rules:{
              phoneNumber:[
                  {required:true,validator:checkPhoneNumber, trigger: 'blur'}
              ],
              password:[
                  {required:true,validator:validatePass,trigger:'blur'}
              ],
              checkpass:[
                  {required:true,validator:validateCheckPass,trigger:'blur'}
              ],
              email:[
                  {required:true,message:'请输入邮箱地址',trigger:'blur'},
                  {type:'email',message:'请输入正确的邮箱地址',trigger:['blur','change']}
              ]
           }
        }
    },
    created(){
    //    var reg = /^(?![0-9]+$)(?![a-zA-Z]+$)(?![`~!@#$%^&*()_\-+=<>?:"{}|,.\/;'\\[\]·~！@#￥%……&*（）——\-+={}|《》？：“”【】、；‘'，。、]+$)[0-9A-Za-z,`~!@#$%^&*()_\-+=<>?:"{}|,.\/;'\\[\]·~！@#￥%……&*（）——\-+={}|《》？：“”【】、；‘'，。、]{8,16}$/
    //    var reg = /^(?![0-9]+$)(?![a-zA-Z]+$)(?![_@#$%^&*]+$)[0-9a-zA-Z_@#$%^&*]{8-16}$/
    //    console.log(reg.test('1234567890&*'))
    },
    methods:{
       login(formName){
           this.$refs[formName].validate((valid) => {
               if(valid){
                   this.$message.success('登录成功')
               }else{
                   return false
               }
           })
       },
       resetForm(formName){
           this.$refs[formName].resetFields();
       }
    }
}
</script>
<style lang="scss" scoped>
  .el-form-item{
      width:460px;
  }
</style>