<template>
    <!--登陆表单的容器-->
    <div class="login-container">
        <!--登陆区域-->
        <div class="login_box">
            <!--头像-->
            <div class="avatar_box">
              <img src="../assets/img/timg.gif" alt="">
            </div>
            <!--表单-->
          <el-form :model="loginForm" :rules="loginRules" ref="loginForm" label-width="0px" class="login_form">
            <el-form-item  prop="username">
              <el-input prefix-icon="el-icon-user-solid" v-model="loginForm.username"></el-input>
            </el-form-item>
            <el-form-item prop="password">
              <el-input prefix-icon="el-icon-lock" v-model="loginForm.password"></el-input>
            </el-form-item>

            <el-form-item>
              <el-button type="primary" @click="submitForm('loginForm')">立即创建</el-button>
              <el-button @click="resetForm('loginForm')">重置</el-button>
            </el-form-item>
          </el-form>
        </div>

    </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      loginForm: {
        username: '',
        password: ''
      },
      loginRules: {
        username: [
          { required: true, message: '请输入用户名', trigger: 'blur' },
          { min: 3, max: 16, message: '长度在 3 到 16 个字符', trigger: 'blur' }
        ],
        password: [
          { required: true, message: '请输入密码', trigger: 'blur' },
          { min: 3, max: 16, message: '长度在 3 到 16 个字符', trigger: 'blur' }
        ]
      }
    };
  },
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
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    }
  }
}
</script>

<style lang="less" scoped>
    .login-container{
        height: 100%;
        background: aquamarine;
    }

    .login_box {
      width: 450px;
      height: 380px;
      background-color: #FFFFFF;
      border-radius: 3px;
      position: absolute;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
    }

    // 该盒子的样式会自动集成父盒子（.login_box）的样式
    .avatar_box {
      width: 130px;
      height: 130px;
      border: 1px solid #eeeeee; // 边框
      border-radius: 50%; // 圆形边框
      padding: 10px; //内边距
      box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1); //阴影
      margin: -65px auto; //外边距，上下-65 左右居中
      background-color: #FFFFFF;

      //层叠样式表
      img {
        width: 100%;
        height: 100%;
        border-radius: 50%; //圆形
        background-color: #eeeeee;
      }
    }

    .login_form {
      position: absolute;
      bottom: 0px;
      width: 100%;
      padding: 0px 20px;
      box-sizing: border-box;
    }
</style>