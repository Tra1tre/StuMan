<template>
    <div>
        <el-header>
            <MainHeader></MainHeader>
        </el-header>
        <h1>登录</h1>
     <div class="login-container">
        <el-form ref="loginForm" :model="loginForm" label-width="80px" class="login-form">
            <el-form-item label="用户名" prop="username">
                <el-input v-model="loginForm.username" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="密码" prop="password">
                <el-input v-model="loginForm.password" type="password" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="submitForm('loginForm')">登录</el-button>
            </el-form-item>
        </el-form>
     </div>
    </div>
</template>

<script>
import axios from 'axios';
import { Notification } from 'element-ui';
import MainHeader from "@/components/MainHeader.vue";

export default {
    name: 'LoginView',
    components:{
      MainHeader
    },
    data() {
        return {
            loginForm: {
                username: '',
                password: ''
            }
        };
    },
    methods: {
        submitForm(formName) {
            this.$refs[formName].validate((valid) => {
                if (valid) {
                    axios.post('/api/login', this.loginForm).then((response) => {
                        if (response.data.code === 0) {
                            Notification.success({
                                title: '登录成功',
                                message: '欢迎回来！'
                            });
                        } else {
                            Notification.error({
                                title: '登录失败',
                                message: response.data.msg
                            });
                        }
                    }).catch((error) => {
                        Notification.error({
                            title: '请求失败',
                            message: error.message
                        });
                    });
                } else {
                    return false;
                }
            });
        }
    }
};
</script>

<style scoped>
.login-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
}

.login-form {
    width: 400px;
}
</style>