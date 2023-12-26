<template>
  <div class="login-container">
    <div class="logo" />
    <div class="form">
      <h1>Login</h1>
      <el-card shadow="never" class="login-card">
        <!--Login From-->
        <el-form ref="form" :model="loginForm" :rules="rules">
          <el-form-item prop="account">
            <el-input
              v-model="loginForm.account"
              placeholder="Please Enter Account Name"
            ></el-input>
          </el-form-item>
          <el-form-item prop="password">
            <el-input
              v-model="loginForm.password"
              show-password
              placeholder="Please Enter Password"
            ></el-input>
          </el-form-item>
          <el-form-item prop="isAgree">
            <el-checkbox v-model="loginForm.isAgree"
              >User Agreement</el-checkbox
            >
          </el-form-item>
          <el-form-item>
            <el-button @click="login" type="primary" style="width: 350px"
              >Login</el-button
            >
          </el-form-item>
        </el-form>
      </el-card>
    </div>
  </div>
</template>
<script>
export default {
  name: "Login",
  data() {
    return {
      loginForm: {
        account: "",
        password: "",
        isAgree: false,
      },
      rules: {
        account: [
          {
            required: true,
            message: "Please Enter Phone Number!",
            trigger: "blur",
          },
          {
            pattern: /^1[3-9]\d{9}$/,
            message: "Please Enter Right Format!",
            trigger: "blur",
          },
        ],
        password: [
          {
            required: true,
            message: "Please Enter Password!",
            trigger: "blur",
          },
          {
            min: 6,
            max: 16,
            message: "Password Length should be 6-16",
            trigger: "blur",
          },
        ],
        isAgree: [
          {
            validator: (rule, value, callback) => {
              value ? callback() : callback(new Error("Please check to agree"));
            },
          },
        ],
      },
    };
  },
  methods: {
    // method for login validate
    login() {
      this.$refs.form.validate((success) => {
        if (success) {
          console.log(11111);
        }
      });
    },
  },
};
</script>
<style lang="scss">
.login-container {
  display: flex;
  align-items: stretch;
  height: 100vh;
  .logo {
    flex: 3;
    background: rgba(38, 72, 176) url(../../assets/common/login_back.png)
      no-repeat center / cover;
    border-top-right-radius: 60px;
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    justify-content: center;
    padding: 0 100px;
    .icon {
      background: url(../../assets/common/logo.png) no-repeat 70px center /
        contain;
      width: 300px;
      height: 50px;
      margin-bottom: 50px;
    }
    p {
      color: #fff;
      font-size: 18px;
      margin-top: 20px;
      width: 300px;
      text-align: center;
    }
  }
  .form {
    flex: 2;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding-left: 176px;
    .el-card {
      border: none;
      padding: 0;
    }
    h1 {
      padding-left: 20px;
      font-size: 24px;
    }
    .el-input {
      width: 350px;
      height: 44px;
      .el-input__inner {
        background: #f4f5fb;
      }
    }
    .el-checkbox {
      color: #606266;
    }
  }
}
</style>
