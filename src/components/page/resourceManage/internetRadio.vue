<template>
    <div>
        <el-container>
            <el-main>
                <div class="top">
                    <el-button type="primary" plain class="add-btn" @click="addRadio()"><i class="fa fa-plus-square"></i>&nbsp; 添加电台</el-button>
                    <el-input
                        placeholder="输入名称或地址搜索"
                        prefix-icon="el-icon-search"
                        v-model="inputSeach">
                    </el-input>
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
                        prop="address"
                        label="地址"
                        header-align="center"
                        >
                        </el-table-column>
                        <el-table-column
                        header-align="center"
                        label="操作"
                        >
                        <template slot-scope="scope">
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
                    <span class="selectSpan">已选择<span>{{multipleSelection.length}}</span>个电台</span>
                    <el-button type="primary" plain class="btn"><i class="fa fa-trash-o"></i> 删除选中电台</el-button>
                </div>
            </el-main>
        </el-container>
        <!-- 弹窗 -->
        <el-dialog title="添加电台" :visible.sync="dialogFormVisible" :close-on-click-modal="false">
            <el-form ref="form" :model="form" label-width="80px" :rules="rules" :status-icon="true">
                <el-form-item label="电台名称" prop="name">
                    <el-input v-model="form.name"></el-input>
                </el-form-item>
                <el-form-item label="电台地址" prop="address">
                    <el-input v-model="form.address"></el-input>
                </el-form-item>
            </el-form>
            <div slot="footer" class="dialog-footer">
                <el-button @click="dialogFormVisible = false">取 消</el-button>
                <el-button type="primary" @click="save">创 建</el-button>
            </div>
        </el-dialog>
    </div>
</template>

<script>
    let data = [
        {
            name:'雨蝶.mp3',
            address:'http://www.baidu.com'
        },
        {
            name:'雨蝶.mp3',
            address:'http://www.baidu.com'
        },
        {
            name:'雨蝶.mp3',
            address:'http://www.baidu.com'
        },
        {
            name:'雨蝶.mp3',
            address:'http://www.baidu.com'
        },
        {
            name:'雨蝶.mp3',
            address:'http://www.baidu.com'
        },
        {
            name:'雨蝶.mp3',
            address:'http://www.baidu.com'
        },
        {
            name:'雨蝶.mp3',
            address:'http://www.baidu.com'
        },
        {
            name:'雨蝶.mp3',
            address:'http://www.baidu.com'
        },
        {
            name:'雨蝶.mp3',
            address:'http://www.baidu.com'
        },
        {
            name:'雨蝶.mp3',
            address:'http://www.baidu.com'
        }
    ]
    export default {
        data() {
            return {
                dialogFormVisible:false,
                tableList:data,
                inputSeach:'',
                selectValue1:'',
                multipleSelection:[],
                pageInfo:{
                    total:100,
                    currentPage: 10,
                },
                form:{
                    name:'',
                    address:''
                },
                rules:{
                    name:[
                        {required:true, message:'请输入电台名称',trigger:'blur'}
                    ],
                    address:[
                        {required:true, message:'请输入电台地址', trigger:'blur'}
                    ]
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
            
            },
            addRadio() {
                this.dialogFormVisible = true;
            },
            save(){
                this.$refs['form'].validate((valid)=>{
                    if(valid) {
                        
                    }
                    else{
                        return false;
                    }
                })
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
    .top .el-input{
        width: auto;
        float: right;
        width: 200px;
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