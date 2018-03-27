<template>
    <div>
        <el-container>
            <el-aside width="360px"></el-aside>
            <el-main>Main</el-main>
        </el-container>
    </div>
</template>

<script>
    export default { 
        data: function(){
            return {}
        }
    }
</script>

<style scoped>
.el-aside {
    /* background-color: #D3DCE6; */
    color: #333;
    text-align: center;
    border: 1px solid #D3DCE6;
    margin-right: 20px;
  }
.el-main {
    /* background-color: #E9EEF3; */
    color: #333;
    text-align: center;
    border: 1px solid #D3DCE6;
}
</style>