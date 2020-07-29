<template>
    <div class="registration">
        <el-container>
            <el-main>
                <div class="from">
                    <el-form :model="ruleForm" status-icon :rules="rules" ref="ruleForm" label-width="100px"
                             class="demo-ruleForm">
                        <el-form-item label="密码" prop="pass">
                            <el-input type="password" v-model="ruleForm.pass" autocomplete="off"></el-input>
                        </el-form-item>
                        <el-form-item label="确认密码" prop="checkPass">
                            <el-input type="password" v-model="ruleForm.checkPass" autocomplete="off"></el-input>
                        </el-form-item>
                        <el-form-item label="年龄" prop="age">
                            <el-input v-model.number="ruleForm.age"></el-input>
                        </el-form-item>
                        <el-form-item>
                            <el-button type="primary" @click="submitForm('ruleForm')">提交</el-button>
                            <el-button @click="resetForm('ruleForm')">重置</el-button>
                        </el-form-item>
                    </el-form>
                </div>
            </el-main>
        </el-container>

    </div>
</template>

<script>
    export default {
        name: 'RegIstration',
        data() {
            var checkAge = (rule, value, callback) => {
                if (!value) {
                    return callback(new Error('年龄不能为空'));
                }
                setTimeout(() => {
                    if (!Number.isInteger(value)) {
                        callback(new Error('请输入数字值'));
                    } else {
                        if (value < 18) {
                            callback(new Error('必须年满18岁'));
                        } else {
                            callback();
                        }
                    }
                }, 1000);
            };
            var validatePass = (rule, value, callback) => {
                if (value === '') {
                    callback(new Error('请输入密码'));
                } else {
                    if (this.ruleForm.checkPass !== '') {
                        this.$refs.ruleForm.validateField('checkPass');
                    }
                    callback();
                }
            };
            var validatePass2 = (rule, value, callback) => {
                if (value === '') {
                    callback(new Error('请再次输入密码'));
                } else if (value !== this.ruleForm.pass) {
                    callback(new Error('两次输入密码不一致!'));
                } else {
                    callback();
                }
            };
            return {
                ruleForm: {
                    pass: '',
                    checkPass: '',
                    age: ''
                },
                rules: {
                    pass: [
                        {validator: validatePass, trigger: 'blur'}
                    ],
                    checkPass: [
                        {validator: validatePass2, trigger: 'blur'}
                    ],
                    age: [
                        {validator: checkAge, trigger: 'blur'}
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
    .hello{

    }
    .el-form{
        border-radius: 15px;
        position: relative;
        top: 140px;
        margin: auto;
        width: 35%;
        height: 25%;
        border-color: black;
        background-image: url("../../public/image/595117b635d94a09a92fcd57d4cb340.png");
        background-size: 100%;
        background-repead:no-repead;
    }

    .el-main {
        background-image: url("https://fuss10.elemecdn.com/a/3f/3302e58f9a181d2509f3dc0fa68b0jpeg.jpeg");
        background-size: 100%;
        background-repead:no-repead;
        text-align: center;
        height: 780px;
        line-height: 160px;
    }
</style>