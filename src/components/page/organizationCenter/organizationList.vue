<template>
    <div>
		<div class="custom-tree-container">
			<el-button style="margin-top:15px;" @click="BtnAdd()"><i class="fa fa-folder-open"></i>&nbsp; 添加机构</el-button>
            <el-button style="margin-top:15px;">
				<i class="fa fa-bookmark"></i>&nbsp; 添加业务组</el-button>
			<div class="block">
				<el-tree
					:data="dataList"
					show-checkbox
					node-key="id"
					:expand-on-click-node="false">
					<span class="custom-tree-node" slot-scope="{ node, data }">
						<span>
                            <i class="fa" :class="data.type === 'oz'?'fa-folder-open':'fa-bookmark'"></i>
                            {{ node.label }}
                        </span>
						<span>
							{{node.type}}
						</span>
						<span>
							<el-button
								type="text"
								size="mini"
								@click="() => append(data)">
								添加
							</el-button>
							<el-button
								type="text"
								size="mini"
								@click="() => edit(node, data)">
								编辑
							</el-button>
							<el-button
								type="text"
								size="mini"
								@click="() => remove(node, data)">
								删除
							</el-button>
						</span>
					</span>
    			</el-tree>
			</div>
		</div>
		<!-- 弹出框 -->
		<el-dialog title="添加机构" :visible.sync="dialogFormVisible">
			<el-form :model="form" :rules="rules1"  ref="form">
				<el-form-item label="机构名称" :label-width="formLabelWidth" prop="name">
					<el-input type="text" v-model="form.name" placeholder="请输入机构名"></el-input>
				</el-form-item>
			</el-form>
			<div slot="footer" class="dialog-footer">
				<el-button @click="dialogFormVisible = false,parentNode = false,childrenNode = false,form.name = ''">取 消</el-button>
				<el-button type="primary" @click ="add('form')">添 加</el-button>
			</div>
		</el-dialog>
		<el-dialog title="编辑机构" :visible.sync="dialogEditVisible">
			<el-form :model="Edit" :rules="rules2" ref="Edit">
				<el-form-item label="机构名称" :label-width="formLabelWidth" prop="name">
					<el-input type="text" v-model="Edit.name" placeholder="请修改机构名"></el-input>
				</el-form-item>
			</el-form>
			<div slot="footer" class="dialog-footer">
				<el-button @click="dialogEditVisible = false,Edit.name = ''">取 消</el-button>
				<el-button type="primary" @click ="SaveEdit('Edit')">修 改</el-button>
			</div>
		</el-dialog>
		<!-- 确认删除提示框 -->
		<!--<el-dialog
			title="提示"
			:visible.sync="dialogVisible"
			width="30%"
			:before-close="handleClose">
			<span>确认删除此机构吗？</span>
			<span slot="footer" class="dialog-footer">
				<el-button @click="dialogVisible = false">取 消</el-button>
				<el-button type="primary" @click="dialogVisible = false">确 定</el-button>
			</span>
		</el-dialog> -->
	</div>
</template>

<script>
    var localData = {
		save(key,value){
			localStorage.setItem(key,JSON.stringify(value));
		},
		getData(key){
			return JSON.parse(localStorage.getItem(key)) || [];
		}
	};
    export default {
		data () {
			const data = localData.getData('data-list') || [];
			return {
				EditIndex:'',
				EditData:[],
				childrenData:[],
				disabl:true,
				parentNode:false,
				childrenNode:false,
				dialogVisible:false,
				dialogEditVisible:false,
				dialogFormVisible: false,
				formLabelWidth: '80px',
				dataList: JSON.parse(JSON.stringify(data)),
				form:{ name:'' },
				Edit:{ name:'' },
				rules1: {
					name: [{ required: true, message: '请输入机构名称', trigger: 'blur' }]
				},
				rules2: {
					name: [{ required: true, message: '机构名称必填', trigger: 'blur' }]
				}
			};
		},
		watch:{
			//深监控
			dataList:{
				handler:function(){
					localData.save("data-list",this.dataList);
				}, 
				deep:true
			}
		},
		methods: {
			append(data) {
				this.parentNode        = false;
				this.childrenNode      = true;
				this.dialogFormVisible = true;
				this.childrenData      = data;
			},
			remove(node, data) {
				const parent   = node.parent;
				const children = parent.data.children || parent.data;
				const index    = children.findIndex(d => d.id === data.id);
				children.splice(index, 1);
			},
			edit(node, data) {
				const parent   = node.parent;
				const children = parent.data.children || parent.data;
				this.dialogEditVisible = true;
				this.Edit.name         = data.label;
				this.EditIndex         = children.findIndex(d => d.id === data.id);
				this.EditData          = children;
			},
			//保持编辑
			SaveEdit(formName) {
				 this.$refs[formName].validate((valid) => {
					 if(valid) {
						 this.EditData[this.EditIndex].label = this.Edit.name;
						 this.dialogEditVisible = false;
						 this.Edit.name = '';
					 }else {
						 return false;
					 }
				 })
			},
			//按钮添加主机构
			BtnAdd() {
				this.parentNode        = true;
				this.dialogFormVisible = true;
				this.childrenNode      = false;
				let name = this.form.name;
			},
			add(formName) {
				this.$refs[formName].validate((valid) => {
					if(valid){
						if(this.parentNode){
							let newChild   = { id: this.dataList.length+1, label:this.form.name ,children : [] ,type:'oz' };
							this.dataList.push(newChild);
						}
						if(this.childrenNode){
							let newChild = { id: (this.childrenData.children.length+1)*10+1, label: this.form.name, children: [] ,type:'oz'};
							if (!this.childrenData.children) {
								this.$set(this.childrenData, 'children', []);
							}
							this.childrenData.children.push(newChild);
						}
						this.form.name = '';
						this.dialogFormVisible = false;
					}else {
						// this.$message.error('必填，请输入机构名！！！');
						return false;
					}
        		});
			}
		}
	}
</script>

<style scoped>
    .custom-tree-node {
		flex: 1;
		display: flex;
		align-items: center;
		justify-content: space-between;
		font-size: 14px;
		padding-right: 8px;
	}
	.block{
		border:1px solid #dcdfe6;
		margin-top:15px;
		padding:10px;
	}
</style>