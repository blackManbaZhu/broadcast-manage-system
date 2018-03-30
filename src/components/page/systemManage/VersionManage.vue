<template>
    <div>
        <el-container>
            <el-main>
                <div class="top">
                    <el-button type="primary" plain class="add-btn"><i class="fa fa-plus-square"></i>&nbsp; 添加版本信息</el-button>
                    <el-select v-model="selectValue3" placeholder="全部型号" class="select">
                        <el-option
                        v-for="item in options3"
                        :key="item.value"
                        :label="item.label"
                        :value="item.value">
                        </el-option>
                    </el-select>
                    <el-select v-model="selectValue2" placeholder="全部状态" class="select">
                        <el-option
                        v-for="item in options2"
                        :key="item.value"
                        :label="item.label"
                        :value="item.value">
                        </el-option>
                    </el-select>
                    <el-select v-model="selectValue1" placeholder="全部类型" class="select">
                        <el-option
                        v-for="item in options1"
                        :key="item.value"
                        :label="item.label"
                        :value="item.value">
                        </el-option>
                    </el-select>
                </div>
                <div class="table">
                    <el-table
                        :data="tableList"
                        height="500"
                        border
                        style="width: 100%;">
                        <el-table-column
                        prop="versionType"
                        label="版本类型"
                        header-align="center"
                        >
                        </el-table-column>
                        <el-table-column
                        prop="model"
                        label="设备型号"
                        header-align="center"
                        >
                        </el-table-column>
                        <el-table-column
                        prop="versionNumber"
                        label="版本号"
                        header-align="center"
                        >
                        </el-table-column>
                        <el-table-column
                        prop="versionAddress"
                        header-align="center"
                        label="版本地址">
                        </el-table-column>
                        <el-table-column
                        prop="versionAddress"
                        header-align="createTime"
                        label="创建时间">
                        </el-table-column>
                        <el-table-column
                        header-align="center"
                        label="操作"
                        >
                        <template slot-scope="scope">
                            <el-button type="text" @click="handleClick(scope.$index, scope.row)"><i class="fa fa-ban"></i></el-button>
                        </template>
                        </el-table-column>
                    </el-table>
                    <!-- 分页 -->
                    <el-pagination
                        style="margin-top:15px;float:right;"
                        background
                        @current-change="handleCurrentChange"
                        :page-size="pageInfo.currentPage"
                        layout="total, prev, pager, next, jumper"
                        :total="pageInfo.total">
                    </el-pagination>
                </div>
            </el-main>
        </el-container>
    </div>
</template>

<script>
    let data = [
        {
            versionType:'终端',
            model:'EB-MCT-SI',
            versionNumber:'6.5.8',
            versionAddress:'http://www.baidu.com',
            createTime:'2018-04-12 12:10:56'
        },
        {
            versionType:'终端',
            model:'EB-MCT-SI',
            versionNumber:'6.5.8',
            versionAddress:'http://www.baidu.com',
            createTime:'2018-04-12 12:10:56'
        },
        {
            versionType:'终端',
            model:'EB-MCT-SI',
            versionNumber:'6.5.8',
            versionAddress:'http://www.baidu.com',
            createTime:'2018-04-12 12:10:56'
        }
    ];
    let option1 = [
            {
                value:'全部类型',
                lable:'0'
            },
            {
                value:'终端',
                lable:'1'
            },
            {
                value:'手机',
                lable:'2'
            },
            {
                value:'平板',
                lable:'3'
            }
    ];
    let option2 = [
            {
                value:'全部状态',
                lable:'0'
            },
            {
                value:'有效',
                lable:'1'
            },
            {
                value:'禁用',
                lable:'2'
            }
    ];
    let option3 = [
            {
                value:'全部型号',
                lable:'0'
            }
    ];
    export default {
        data() {
            return {
                options1:option1,
                options2:option2,
                options3:option3,
                tableList:data,
                selectValue1:'',
                selectValue2:'',
                selectValue3:'',
                pageInfo:{
                    total:100,
                    currentPage: 10,
                }
            }
        },
        methods:{
            handleCurrentChange(val) {

            },
            handleClick(index,row) {
            
            }
        }
    }
</script>

<style scoped>
    .el-main {
        height: 620px;
        color: #333;
        padding: 0;
        overflow: none;
        border: 1px solid #D3DCE6;
    }
    .top{
        width: 100%;
        height: 50px;
        border-bottom: 1px solid #D3DCE6;
        padding-top: 5px;
    }
    .add-btn{
        margin-left: 10px;
    }
    .el-input{
        width: auto;
        float: right;
        width: 150px;
        margin-right: 10px;
    }
    .select{
        width: 120px;
        margin-right: 10px;
        color: #409EFF;
        float: right;
    }
    .table{
        width: 100%;
        height: 556px;
        padding: 5px;
        text-align: center;
    }
    .table i.fa{
        font-size: 18px;
    }
</style>