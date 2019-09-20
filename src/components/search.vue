<template>
    <div>
        <div class="input-search">
            <el-autocomplete  :fetch-suggestions="querySearch" v-model="searchValue" placeholder="请输入搜索内容">
                <el-button slot="append" icon="el-icon-search"></el-button>
            </el-autocomplete>
        </div>
    </div>
</template>
<script>
export default {
    data(){
        return {
           searchValue:'',
           inputSuggestion:[]
        }
    },
    methods:{
      querySearch(queryString){
          
      }
    }
}
</script>
<style scoped>
    .input-search .el-input{
        width:500px;
    }
</style>