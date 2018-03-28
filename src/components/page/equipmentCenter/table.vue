<template>
    <div>
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
            label="设备名称"
            header-align="center"
            width="180">
            </el-table-column>
            <el-table-column
            prop="code"
            label="设备编号"
            header-align="center"
            width="180">
            </el-table-column>
            <el-table-column
            prop="network"
            header-align="center"
            label="网络类型">
            </el-table-column>
            <el-table-column
            prop="status"
            header-align="center"
            label="状态">
            </el-table-column>
            <el-table-column
            prop="signal"
            header-align="center"
            label="信号">
            <i class="fa fa-circle"></i>
            </el-table-column>
            <el-table-column
            prop="versions"
            header-align="center"
            label="版本号">
            </el-table-column>
            <el-table-column
            header-align="center"
            label="操作"
            >
             <template slot-scope="scope">
                <el-button @click="handleClick(scope.$index, scope.row)" type="text"><i class="fa fa-file-text"></i></el-button>
                <el-button type="text"><i class="fa fa-file-text-o"></i></el-button>
            </template>
            </el-table-column>
        </el-table>
        <el-pagination
            style="margin-top:15px;float:right;"
            background
            @current-change="handleCurrentChange"
            :page-size="pageInfo.currentPage"
            layout="total, prev, pager, next, jumper"
            :total="pageInfo.total">
        </el-pagination>
    </div>
</template>

<script>
export default {
    props:[
        'tableData'
    ],
    data() {
        return {
            tableList:this.tableData,
            multipleSelection:[],
            pageInfo:{
				total:100,
				currentPage: 10,
			}, 
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

</style>


