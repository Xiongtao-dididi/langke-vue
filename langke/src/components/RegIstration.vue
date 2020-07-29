<template>
    <div class="registration">
        <el-container>
            <el-main>
                <h1 style=" font-family: '隶书';font-size:100px;  text-shadow:5px -5px 2px gray">浪客</h1>
                <div class="from">
                    <el-form :model="ruleForm" status-icon :rules="rules" ref="ruleForm" label-width="100px"
                             class="demo-ruleForm">
                        <el-form-item label="用户名" prop="username">
                            <el-input v-model="ruleForm.username" autocomplete="off"></el-input>
                        </el-form-item>
                        <el-form-item label="密码" prop="pass">
                            <el-input type="password" v-model="ruleForm.pass" autocomplete="off"></el-input>
                        </el-form-item>
                        <el-form-item>
                            <el-button type="primary" @click="submitForm('ruleForm')">登录</el-button>
                            <el-button @click="resetForm('ruleForm')">重置</el-button>
                            <div class="login">
                                <span>没有账号？</span>
                                <el-button type="text" @click="dialogVisible = true">注册</el-button>
                            </div>
                        </el-form-item>
                    </el-form>
                    <el-dialog  :visible.sync="dialogVisible" width="30%">
                        <h1 style="font-family: '隶书';font-size:50px;margin-top: -65px">注册</h1>
                        <el-form class="zhucei" ref="form" :model="form" status-icon :rules="rules2" label-width="80px">
                            <el-form-item label="用户名"  prop="username2">
                                <el-input v-model="form.username2"  autocomplete="off"></el-input>
                            </el-form-item>
                            <el-form-item label="密码" prop="pass2">
                                <el-input type="password" v-model="form.pass2"  autocomplete="off"></el-input>
                            </el-form-item>
                            <el-form-item label="姓名" prop="realname">
                                <el-input v-model="form.realname"  autocomplete="off"></el-input>
                            </el-form-item>
                            <el-form-item label="号码" prop="number">
                                <el-input v-model="form.number"  autocomplete="off"></el-input>
                            </el-form-item>
                            <el-form-item label="性别">
                                <el-radio v-model="form.radio" label="1">男</el-radio>
                                <el-radio v-model="form.radio" label="2">女</el-radio>
                            </el-form-item>
                        </el-form>
                        <div style="margin-top: -80px" slot="footer" class="dialog-footer">
                      <el-button @click="dialogVisible = false">取 消</el-button>
                      <el-button type="primary" @click="dialogVisible = false">确 定</el-button>
                        </div>
                    </el-dialog>

                </div>
            </el-main>
        </el-container>

    </div>
</template>
<script>
    export default {
        name: 'RegIstration',
        data() {
            var validatePass = (rule, value, callback) => {
                if (value === '') {
                    callback(new Error('请输入用户名'));
                } else {
                    callback();
                }
            };
            var validatePass2 = (rule, value, callback) => {
                if (value === '') {
                    callback(new Error('请输入密码'));
                } else {
                    callback();
                }
            };
            var username2 = (rule, value, callback) => {
                if (value === '') {
                    callback(new Error('请输入用户名'));
                } else {
                    callback();
                }
            };
            var number = (rule, value, callback) => {
                if (value === '') {
                    callback(new Error('请输入电话号码'));
                } else {
                    callback();
                }
            };
            var realname = (rule, value, callback) => {
                if (value === '') {
                    callback(new Error('请输入姓名'));
                } else {
                    callback();
                }
            };
            var pass2 = (rule, value, callback) => {
                if (value === '') {
                    callback(new Error('请输入密码'));
                } else {
                    callback();
                }
            };
            return {
                dialogVisible: false,
                form: {
                    number: '',
                    radio: '1',
                    realname:'',
                    username2: '',
                    pass2:''

                },
                ruleForm: {
                    username: '',
                    pass: '',
                },
                rules: {
                    username: [
                        {validator: validatePass, trigger: 'blur'}
                    ],
                    pass: [
                        {validator: validatePass2, trigger: 'blur'}
                    ]
                },
                rules2: {
                    username2: [
                        {validator: username2, trigger: 'blur'}
                    ],
                    pass2: [
                        {validator: pass2, trigger: 'blur'}
                    ],
                    number: [
                        {validator: number, trigger: 'blur'}
                    ],
                    realname: [
                        {validator: realname, trigger: 'blur'}
                    ]
                }
            };
        }
        ,
        methods: {
            submitForm(formName) {
                this.$refs[formName].validate((valid) => {
                    if (valid) {
                        alert('submit!');
                    } else {
                        console.log('error submit!!');
                        return false;
                    }
                });
            }
            ,
            resetForm(formName) {
                this.$refs[formName].resetFields();
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .dialog-footer .el-button{
        margin-top: -50px;
        width: 150px;
    }
.dialog-footer{
   margin-right:75px;
}
    .zhucei{
        margin-bottom: 50px;
    }
    .zhucei .el-input {
        width: 350px;

    }
    .zhucei .el-form-item{
        margin-left: -145px;
    }
.zhucei .el-radio{
    margin-left: 60px;
}
    .from .el-form {
        border-radius: 15px;
        position: relative;
        margin: auto;
        bottom: 80px;
        width: 35%;
        height: 25%;
        border-color: black;
        /*background-image: url("../../public/image/595117b635d94a09a92fcd57d4cb340.png");*/
        background-size: 100%;
        background-repead: no-repead;
    }
    .login{
        margin-right: 350px;
    }
    .login .el-button{
        width: 10px;
    }
    .el-main {
        margin-top: -60px;
        background-image: url("../../public/image/595117b635d94a09a92fcd57d4cb340.png");
        /*background-size: 100%;*/
        /*background-repead:no-repead;*/
        text-align: center;
        height: 844px;
        line-height: 160px;
    }

    .el-button {
        width: 240px;
    }
</style>