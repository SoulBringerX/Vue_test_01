<template>
  <div class="auth-container">
    <div v-if="isLogin" class="form-container">
      <h2 id="login">登录</h2>
      <form @submit.prevent="handleLogin">
        <div class="form-group">
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
    handleLogin() {
      // 这里添加登录逻辑，例如调用 API
      console.log('Login form submitted:', this.loginForm)
      if (this.loginForm.account == '123' && this.loginForm.password == '123') {
        this.isLogin = false
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
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
}

.form-container {
  background-color: #f9f9f9;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.form-group {
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
  text-align: center;
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
