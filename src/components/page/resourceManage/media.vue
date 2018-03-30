<template>
    <div>
        <el-container>
            <el-main>
                <div class="top">
                    <el-button type="primary" plain class="add-btn"><i class="fa fa-plus-square"></i>&nbsp; 添加音频</el-button>
                    <el-input
                        placeholder="请输入名称搜索"
                        prefix-icon="el-icon-search"
                        v-model="inputSeach">
                    </el-input>
                    <el-select v-model="selectValue1" placeholder="音频类型" class="select">
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
                        height="450"
                        border
                        style="width: 100%;"
                        @selection-change="handleSelectionChange">
                        <el-table-column
                        type="selection"
                        header-align="center"
                        width="45">
                        </el-table-column>
                        <el-table-column
                        prop="name"
                        label="名称"
                        header-align="center"
                        width="180">
                        </el-table-column>
                        <el-table-column
                        prop="creator"
                        label="创建人"
                        header-align="center"
                        width="180">
                        </el-table-column>
                        <el-table-column
                        prop="createTime"
                        header-align="center"
                        label="创建时间">
                        </el-table-column>
                        <el-table-column
                        header-align="center"
                        label="操作"
                        >
                        <template slot-scope="scope">
                            <el-button type="text"><i class="fa fa-play-circle"></i></el-button>
                            <el-button type="text" @click="handleClick(scope.$index, scope.row)"><i class="fa fa-edit"></i></el-button>
                            <el-button type="text"><i class="fa fa-trash-o"></i></el-button>
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
                <div class="bottom">
                    <span class="selectSpan">已选择<span>0</span>个音频</span>
                    <el-button type="primary" plain class="btn"><i class="fa fa-trash-o"></i> 删除选中音频</el-button>
                </div>
            </el-main>
        </el-container>
    </div>
</template>

<script>
    let data = [
        {
            name:'雨蝶.mp3',
            creator:'xx-xx',
            createTime:'2018-04-12 12:10:56'
        },
        {
            name:'雨蝶.mp3',
            creator:'xx-xx',
            createTime:'2018-04-12 12:10:56'
        },
        {
            name:'雨蝶.mp3',
            creator:'xx-xx',
            createTime:'2018-04-12 12:10:56'
        },
        {
            name:'雨蝶.mp3',
            creator:'xx-xx',
            createTime:'2018-04-12 12:10:56'
        },
        {
            name:'雨蝶.mp3',
            creator:'xx-xx',
            createTime:'2018-04-12 12:10:56'
        },
        {
            name:'雨蝶.mp3',
            creator:'xx-xx',
            createTime:'2018-04-12 12:10:56'
        },
        {
            name:'雨蝶.mp3',
            creator:'xx-xx',
            createTime:'2018-04-12 12:10:56'
        },
        {
            name:'雨蝶.mp3',
            creator:'xx-xx',
            createTime:'2018-04-12 12:10:56'
        },
        {
            name:'雨蝶.mp3',
            creator:'xx-xx',
            createTime:'2018-04-12 12:10:56'
        }
    ]
    let options = [
            {
                value:'全部音频',
                lable:'0'
            },
            {
                value:'录音音频',
                lable:'1'
            },
            {
                value:'上传音频',
                lable:'2'
            }
        ]
    export default {
        data() {
            return {
                options1:options,
                tableList:data,
                inputSeach:'',
                selectValue1:'',
                multipleSelection:[],
                pageInfo:{
                    total:100,
                    currentPage: 10,
                }
            }
        },
        methods:{
            handleSelectionChange(val) {
                this.multipleSelection = val;
            },
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
        height: 516px;
        padding: 5px;
        text-align: center;
    }
    .table i.fa{
        font-size: 18px;
    }
    .bottom{
        width: 100%;
        height: 50px;
        border-top: 1px solid #D3DCE6;
    }
    .bottom .btn{
        margin-top: 5px;
        margin-right: 10px;
        float: right;
    }
    .selectSpan{
        float: left;
        margin-left: 10px;
        font-size: 14px;
        line-height: 50px;
    }
</style>