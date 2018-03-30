
<template>
    <div>
        <div class="top">
            <el-button type="primary" plain class="btn">返回</el-button>
            <div class="tip"><span>多设备操作</span>&nbsp;/&nbsp;<span>设备型号</span></div>
        </div>
        <el-container>
            <el-main>Main</el-main>
            <el-aside width="30%">Aside</el-aside>
        </el-container>
    </div>
</template>

<script>
export default {
   data() {
       return{

       }
   }
}
</script>

<style scoped>
.top{
    height: 50px;
}
.top .btn{
    float: left;
}
.top .tip{
    line-height: 40px;
    font-size: 14px;
    color: #606266;
    float: right;
}
.el-aside {
    height: 70vh;
    color: #333;
    padding: 0;
    border: 1px solid #D3DCE6;
    margin-left: 20px;
  }
.el-main {
    color: #333;
    padding: 0;
    border: 1px solid #D3DCE6;
}
</style>

