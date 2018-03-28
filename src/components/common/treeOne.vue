<template>
    <div class="tree">
        <el-tree 
        :data="data" 
        :props="defaultProps" 
        @node-click="handleNodeClick"
        :expand-on-click-node="false"
        >
        <span class="custom-tree-node" slot-scope="{ node, data }">
            <span>
                 <i class="fa" :class="data.type ==='oz'?'fa-folder-open':'fa-bookmark'"></i>
                {{node.label}}
            </span>
        </span>
        </el-tree>
    </div>
</template>

<script>
    export default {
        props:[
            'datalist'
        ],
        data() {
            return {
                data:this.datalist,
                defaultProps: {
                    children: 'children',
                    label: 'label',
                    id:100
                }
            }
        },
        methods:{
            handleNodeClick(data) {
                console.log(data.type);
            }
        }
    }
</script>

<style scoped>
    .tree{
        padding: 20px;
    }
</style>