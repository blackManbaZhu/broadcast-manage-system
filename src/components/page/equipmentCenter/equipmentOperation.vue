<template>
    <div>
        <el-container>
            <el-aside width="360px" class="left">
                <div class="tree">
                    <v-tree :datalist="treeList"></v-tree>
                </div>
                <div class="bottom">
                    <el-button type="info" plain>机构直播</el-button>
                    <el-button type="info" plain>批量机构操作</el-button>
                </div>
            </el-aside>
            <el-main class="right">
                <div class="top">
                    <el-select v-model="selectValue3" placeholder="显示数目" class="select">
                        <el-option
                        v-for="item in options3"
                        :key="item"
                        :label="item"
                        :value="item">
                        </el-option>
                    </el-select>
                    <el-input
                        placeholder="名称和编号搜索"
                        prefix-icon="el-icon-search"
                        v-model="inputSeach">
                    </el-input>
                    <el-select v-model="selectValue2" placeholder="全部状态" class="select">
                        <el-option
                        v-for="item in options2"
                        :key="item.value"
                        :label="item.label"
                        :value="item.value">
                        </el-option>
                    </el-select>
                    <el-select v-model="selectValue1" placeholder="网络类型" class="select">
                        <el-option
                        v-for="item in options1"
                        :key="item.value"
                        :label="item.label"
                        :value="item.value">
                        </el-option>
                    </el-select>
                </div>
                <div class="table">
                    <v-table :tableData="tableList"></v-table>
                </div>
                <div class="bottom">
                    <span class="selectSpan">已选择<i>0</i>个设备</span>
                    <el-button type="primary" plain>进入直播</el-button>
                    <el-button type="primary" plain>操作选中设备</el-button>
                </div>
            </el-main>
        </el-container>
    </div>
</template>

<script>
    import vTree  from '../../common/treeOne.vue';
    import vTable from "./table.vue";
    export default { 
        components:{
            vTree,vTable
        },
        data() {
            return {
                selectValue1:'',
                selectValue2:'',
                selectValue3:'',
                inputSeach:'',
                treeList:[],
                tableList:[
                    {
                        name:'设备1',
                        code:'01',
                        network:'有线',
                        status:'离线',
                        signal:0,
                        versions:'v1.1.1'
                    },
                    {
                        name:'设备1',
                        code:'01',
                        network:'有线',
                        status:'离线',
                        signal:0,
                        versions:'v1.1.1'
                    },
                    {
                        name:'设备1',
                        code:'01',
                        network:'有线',
                        status:'离线',
                        signal:0,
                        versions:'v1.1.1'
                    },
                    {
                        name:'设备1',
                        code:'01',
                        network:'有线',
                        status:'离线',
                        signal:0,
                        versions:'v1.1.1'
                    },
                    {
                        name:'设备1',
                        code:'01',
                        network:'有线',
                        status:'离线',
                        signal:0,
                        versions:'v1.1.1'
                    },
                    {
                        name:'设备1',
                        code:'01',
                        network:'有线',
                        status:'离线',
                        signal:0,
                        versions:'v1.1.1'
                    },
                    {
                        name:'设备1',
                        code:'01',
                        network:'有线',
                        status:'离线',
                        signal:0,
                        versions:'v1.1.1'
                    },
                    {
                        name:'设备1',
                        code:'01',
                        network:'有线',
                        status:'离线',
                        signal:0,
                        versions:'v1.1.1'
                    },
                    {
                        name:'设备1',
                        code:'01',
                        network:'有线',
                        status:'离线',
                        signal:0,
                        versions:'v1.1.1'
                    },
                    {
                        name:'设备1',
                        code:'01',
                        network:'有线',
                        status:'离线',
                        signal:0,
                        versions:'v1.1.1'
                    },
                    {
                        name:'设备1',
                        code:'01',
                        network:'有线',
                        status:'离线',
                        signal:0,
                        versions:'v1.1.1'
                    }
                    
                ],
                options1:[
                    {
                        value:'全部',
                        label:'全部'
                    },
                    {
                        value:'有线',
                        label:'有线'
                    },
                    {
                        value:'3/4G网络',
                        label:'3/4G网络'
                    },
                    {
                        value:'适配器',
                        label:'适配器'
                    },
                    {
                        value:'物联网',
                        label:'物联网'
                    }
                ],
                options2:[
                    {
                        value:'全部状态',
                        label:'全部状态'
                    },
                    {
                        value:'在线',
                        label:'在线'
                    },
                    {
                        value:'在播',
                        label:'在播'
                    },
                    {
                        value:'下载',
                        label:'下载'
                    },
                    {
                        value:'锁定',
                        label:'锁定'
                    },
                    {
                        value:'离线',
                        label:'离线'
                    }
                ],
                options3:[ 10, 20, 50, 100]
            }
        },
        created() {
            this.initdata();
        },
        methods:{
            initdata() {
                const list = JSON.parse(localStorage.getItem('data-list')) || [];
                this.treeList = list;
            }
        }
    }
</script>

<style scoped>

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
    /* background-color: #D3DCE6; */
    overflow: none;
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