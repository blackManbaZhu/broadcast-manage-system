<template>
    <div>
         <el-container>
            <el-aside width="360px" class="left">
                <div class="tree">
                    <v-tree :datalist="treeList"></v-tree>
                </div>
                <div class="bottom"></div>
            </el-aside>
            <el-main class="right">
                <div class="top">
                    <el-button style="margin-left:10px;" type="primary" plain><i class="fa fa-plus-square"></i>&nbsp; 添加用户</el-button>
                    <el-button type="primary" plain><i class="fa fa-plus-square"></i>&nbsp; 批量添加</el-button>
                    <el-input
                        placeholder="用户名和手机号搜索"
                        prefix-icon="el-icon-search"
                        v-model="inputSeach">
                    </el-input>
                    <el-select v-model="selectValue" placeholder="全部状态" class="select">
                        <el-option
                        v-for="item in options"
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
                        prop="phone"
                        label="手机号"
                        header-align="center"
                        >
                        </el-table-column>
                        <el-table-column
                        prop="username"
                        label="用户名"
                        header-align="center"
                        >
                        </el-table-column>
                        <el-table-column
                        prop="addTime"
                        header-align="center"
                        label="添加时间">
                        </el-table-column>
                        <el-table-column
                        prop="status"
                        header-align="center"
                        label="状态">
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
                    <span class="selectSpan">已选择<span>0</span>个用户</span>
                    <el-button type="primary" plain>重置选中用户密码</el-button>
                    <el-button type="primary" plain><i class="fa fa-trash-o"></i> 删除选中用户</el-button>
                </div>
            </el-main>
        </el-container>
    </div>
</template>

<script>
    import vTree  from '../../common/treeOne.vue';
    let dataList = [
        {
            phone:'18070902323',
            username:'zhu',
            addTime:'2018-04-06 03:00:58',
            status:'有效'
        },
        {
            phone:'18070902323',
            username:'zhu',
            addTime:'2018-04-06 03:00:58',
            status:'有效'
        },
        {
            phone:'18070902323',
            username:'zhu',
            addTime:'2018-04-06 03:00:58',
            status:'有效'
        },
        {
            phone:'18070902323',
            username:'zhu',
            addTime:'2018-04-06 03:00:58',
            status:'有效'
        },
        {
            phone:'18070902323',
            username:'zhu',
            addTime:'2018-04-06 03:00:58',
            status:'有效'
        },
        {
            phone:'18070902323',
            username:'zhu',
            addTime:'2018-04-06 03:00:58',
            status:'有效'
        },
        {
            phone:'18070902323',
            username:'zhu',
            addTime:'2018-04-06 03:00:58',
            status:'有效'
        },
        {
            phone:'18070902323',
            username:'zhu',
            addTime:'2018-04-06 03:00:58',
            status:'有效'
        },
        {
            phone:'18070902323',
            username:'zhu',
            addTime:'2018-04-06 03:00:58',
            status:'有效'
        }
    ];
    let option = [
        {
            value:'0',
            label:'全部状态'
        },
        {
            value:'1',
            label:'停用'
        },
        {
            value:'2',
            label:'有效'
        }
    ]
    export default { 
        components:{
            vTree
        },
        data() {
            return {
                tableList:dataList,
                options:option,
                selectValue:'',
                inputSeach:'',
                treeList:[],
                multipleSelection:[],
                pageInfo:{
                    total:100,
                    currentPage: 10,
                }, 
            }
        },
        created() {
            this.initdata();
        },
        methods:{
            initdata() {
                const list = JSON.parse(localStorage.getItem('data-list')) || [];
                this.treeList = list;
            },
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
    .el-input{
    width: auto;
    float: right;
    width: 180px;
    margin-right: 10px;
}
.select{
    width: 120px;
    margin-right: 10px;
    color: #409EFF;
    float: right;
}

.left{
    width: 360px;
    height: 620px;
    position: relative;
}
.left .tree{
    width: 100%;
    overflow :auto;
    height: 546px;
}
.right{
    position: relative;
}
.right .top{
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 50px;
    border-bottom: 1px solid #D3DCE6;
    padding-top: 5px;
}
.left .bottom,.right .bottom{
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 60px;
    border-top: 1px solid #D3DCE6;
    padding-top: 10px;
}
.right .bottom{
    text-align: right;
    padding-right: 10px;
}
.right .table{
    text-align: center;
}
.selectSpan{
    float: left;
    margin-left: 10px;
    font-size: 14px;
    line-height: 40px;
}
.selectSpan i{
    color: #3e3e3e;
}
.table{
    position: absolute;
    width: 99%;
    left: 0.5%;
    top: 55px;
}
.el-aside {
    overflow: none;
    color: #333;
    text-align: center;
    border: 1px solid #D3DCE6;
    margin-right: 20px;
  }
.el-main {
    color: #333;
    border: 1px solid #D3DCE6;
}
</style>