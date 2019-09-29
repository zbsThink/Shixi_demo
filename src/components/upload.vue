<template>
    <div>
        <el-upload action="https://jsonplaceholder.typicode.com/posts/" 
        :auto-upload="false" ref="upload" list-type="picture-card" 
        :file-list="fileLists">
          <i  slot="trigger" class="el-icon-plus"></i>
          <el-button type="success" size="small" @click="submitImg">上传图片</el-button>
        </el-upload>
    </div>
</template>
<script>
export default {
    data(){
        return {
           fileLists:[]
        }
    },
    methods:{
        submitImg(){
            this.$refs.upload.submit()
        }
    }
}
</script>
<style scoped>
    
</style>