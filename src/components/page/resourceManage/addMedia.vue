<template>
    <div>
        <el-dialog title="添加音频文件" :visible.sync="addMedia" :show-close="false" :close-on-click-modal="false">
            <!-- <el-form :model="form"> -->
                <el-upload
                    ref="upload"
                    action="https://jsonplaceholder.typicode.com/posts/"
                    :before-upload="beforeUpload"
                    :on-remove="onRemove"
                    :on-exceed="handleExceed"
                    :auto-upload="false"
                    :limit="1"
                    accept=".mp3,.m4a,.wav,.wma,.ogg,.amr,.3gp"
                    >
                    <el-button size="small" type="primary">选择文件</el-button>
                    <div slot="tip" class="el-upload__tip">只能上传mp3/m4a/wav/wma/ogg/amr/3gp文件</div>
                </el-upload>
            <!-- </el-form> -->
            <div slot="footer" class="dialog-footer">
                <el-button @click="cancel">取 消</el-button>
                <el-button type="success" @click="submitUpload">上 传</el-button>
                <el-button type="primary" @click="save">创 建</el-button>
            </div>
        </el-dialog>
    </div>
</template>

<script>
    export default {
        props:[
            'addMedia'
        ],
        data() {
            return {
                fileType:''
            }
        },
        methods:{
            handleExceed(files, fileList) { //选择限制
                // console.log(files);
                this.$message.warning(`当前限制选择1个文件`);
            },
            onRemove() {
                this.fileType = '';
            },
            beforeUpload(file) { //上传之前
                this.fileType = file.name.split('.')[1];
                if(this.fileType != 'mp3' && this.fileType != 'm4a' && this.fileType != 'wav'
                && this.fileType != 'wma' && this.fileType != 'ogg' && this.fileType != 'amr'
                && this.fileType != '3gp'
                ){
                    this.$message.error(`添加失败！当前文件格式不正确!`);
                    this.fileType = '';
                    return false;
                }
            },
            submitUpload() {
                 this.$refs.upload.submit();
            },
            save() {
                this.$emit('close');
            },
            cancel() {
                this.$emit('close');
            }
        }
    }
</script>

<style  scoped>

</style>
