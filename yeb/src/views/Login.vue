<template>
    <div>
        <el-form :rules="rules" ref="loginForm" :model="loginForm" class="loginContainer">
            <h3 class="loginTitle">系统登陆</h3>
            <el-form-item prop="username">
                <el-input type="text" auto-complete="false" v-model="loginForm.username" placeholder="请输入用户名">
                </el-input>
            </el-form-item>
            <el-form-item prop="password">
                <el-input type="password" auto-complete="false" v-model="loginForm.password" placeholder="请输入密码">
                </el-input>
            </el-form-item>
            <el-form-item prop="code">
                <el-input type="text" v-model="loginForm.code" placeholder="点击图片更换验证码"
                    style="width:250px; margin-right: 5px;"></el-input>
                <img :src="captchaUrl">
            </el-form-item>
            <el-checkbox v-model="checked" class="loginRememberMe">记住我</el-checkbox>
            <el-button type="primary" style="width: 100%" @click="submitLogin">登录</el-button>
        </el-form>
    </div>
</template>

<script>
export default {
    name: "Login",
    data() {
        return {
            captchaUrl: '',
            loginForm: {
                username: "admin",
                password: "123456",
                code: ''

            },
            checked: true,
            rules: {
                username: [{ required: true, message: '请输入用名', trigger: 'blur' }],
                password: [{ required: true, message: '请输入密码', trigger: 'blur' }],
                code: [{ required: true, message: '请输入验证码', trigger: 'blur' }]
            }
        };
        },
    methods: {
        submitLogin(){
            this.$refs.loginForm.validate((valid) => {
                if (valid) {
                    alert('submit!');
                } else {
                    this.$message.error('请输入所以字段');
                    return false;
                }
            });
        }
    }
}
</script>

<style>
    .loginContainer{
        border-radius: 15px;
        background-clip: padding-box;
        margin: 180px auto;
        width: 350px;
        padding: 15px 35px 15px 35px;
        background: white;
        border: 1px solid black;
        box-shadow: 0 0 25px #cac6c6;
    }
    .loginTitle {
        margin: 0px auto 40px auto;
        text-align: center;
    }
    .loginRememberMe{
        text-align: left;
        margin: 0px 0px 15px 0px;
    }

</style>