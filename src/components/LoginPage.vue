<template>
  <div class="auth-container">
    <div v-if="isLogin" class="form-container">
      <h2 class="login">登录</h2>
      <form @submit.prevent="handleLogin">
        <div class="form-group">
          <img id="account-image" src="../assets/用户.png">
          <label for="login-account">Account:</label>
          <input type="text" id="login-account" v-model="loginForm.account" required />
        </div>
        <div class="form-group">
          <label for="login-password">Password:</label>
          <input type="password" id="login-password" v-model="loginForm.password" required />
        </div>
        <button type="submit">Login</button>
      </form>
      <p class="switch-link" @click="switchToRegister">目前还没有账号？注册一个</p>
    </div>

    <div v-else class="form-container">
      <h2>注册</h2>
      <form @submit.prevent="handleRegister">
        <div class="form-group">
          <label for="register-name">Name:</label>
          <input type="text" id="register-name" v-model="registerForm.nickname" required />
        </div>
        <div class="form-group">
          <label for="register-email">Email:</label>
          <input type="email" id="register-email" v-model="registerForm.account" required />
        </div>
        <div class="form-group">
          <label for="register-password">Password:</label>
          <input type="password" id="register-password" v-model="registerForm.password" required />
        </div>
        <button type="submit">Register</button>
      </form>
      <p class="switch-link" @click="switchToLogin">已经有账号了！登录</p>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
// import  axios from 'axios'
export default defineComponent({
  data() {
    return {
      isLogin: true,
      loginForm: {
        account: '',
        password: '',
      },
      registerForm: {
        nickname: '',
        account: '',
        password: '',
      },
    }
  },
  methods: {
    async handleLogin() {
      // 这里添加登录逻辑，例如调用 API
      console.log('Login form submitted:', this.loginForm)
      try {
        // const response = await axios.post('http://localhost:8001/api/login', this.loginForm);
        // if (response.data) {
        //   // 登录成功
        //   localStorage.setItem('userInfo', JSON.stringify(this.loginForm.account));

        //   // 跳转到首页或其他页面
        //   this.$router.push('/home'); //拿跳转到首页尝试
        // }
        this.$router.push('/home'); //拿跳转到首页尝试
      } catch (error) {
        console.error('Login failed:', error);
        // 可提示用户登录失败
      }
    },
    handleRegister() {
      // 这里添加注册逻辑，例如调用 API
      console.log('Register form submitted:', this.registerForm)
      // 示例：清空表单
      this.registerForm.nickname = ''
      this.registerForm.account = ''
      this.registerForm.password = ''
    },
    switchToRegister() {
      this.isLogin = false
    },
    switchToLogin() {
      this.isLogin = true
    },
  },
})
</script>

<style scoped>
.auth-container {
  max-width: 100%;
  width: 70%;
  margin: 0 auto;
}

.form-container {
  background-color: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.form-group {
  width: 60%;
  margin-left: 40%;
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input {
  width: 100%;
  padding: 8px;
  box-sizing: border-box;
}

button {
  width: 100%;
  padding: 10px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #3aa57c;
}

.login {
  width: 100%;
  justify-content: center; /* 水平居中 */
}

.switch-link {
  text-align: center;
  margin-top: 15px;
  cursor: pointer;
  color: #42b983;
}

.switch-link:hover {
  text-decoration: underline;
}
</style>
