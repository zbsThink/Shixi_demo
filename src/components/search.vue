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
           inputSuggestions:[{"value":"三鲜小龙虾","address":"上海五福路"},
           { "value": "三全鲜食（北新泾店）", "address": "长宁区新渔路144号" },
          { "value": "Hot honey 首尔炸鸡（仙霞路）", "address": "上海市长宁区淞虹路661号" },
          { "value": "新旺角茶餐厅", "address": "上海市普陀区真北路988号创邑金沙谷6号楼113" }]
        }
    },
    methods:{
      querySearch(queryString,cb){
         var inputSuggestions = this.inputSuggestions;
         var result = queryString ? inputSuggestions.filter(this.createFilter(queryString)) : inputSuggestion;
         cb(result)
      },
      createFilter(queryString){
         return (inputSuggestion) => {
            return inputSuggestion.value.toLowerCase().indexOf(queryString) !== -1
         } 
      }
    }
}
</script>
<style scoped>
    .input-search .el-input{
        width:500px;
    }
</style>