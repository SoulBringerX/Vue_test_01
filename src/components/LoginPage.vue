<template>
  <div class="auth-container">
    <div v-if="isLogin" class="form-container">
      <h2>Login</h2>
      <form @submit.prevent="handleLogin">
        <div class="form-group">
          <label for="login-email">Email:</label>
          <input type="email" id="login-email" v-model="loginForm.email" required />
        </div>
        <div class="form-group">
          <label for="login-password">Password:</label>
          <input type="password" id="login-password" v-model="loginForm.password" required />
        </div>
        <button type="submit">Login</button>
      </form>
      <p class="switch-link" @click="switchToRegister">Don't have an account? Register</p>
    </div>

    <div v-else class="form-container">
      <h2>Register</h2>
      <form @submit.prevent="handleRegister">
        <div class="form-group">
          <label for="register-name">Name:</label>
          <input type="text" id="register-name" v-model="registerForm.name" required />
        </div>
        <div class="form-group">
          <label for="register-email">Email:</label>
          <input type="email" id="register-email" v-model="registerForm.email" required />
        </div>
        <div class="form-group">
          <label for="register-password">Password:</label>
          <input type="password" id="register-password" v-model="registerForm.password" required />
        </div>
        <button type="submit">Register</button>
      </form>
      <p class="switch-link" @click="switchToLogin">Already have an account? Login</p>
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
        email: '',
        password: '',
      },
      registerForm: {
        name: '',
        email: '',
        password: '',
      },
    }
  },
  methods: {
    handleLogin() {
      // 这里添加登录逻辑，例如调用 API
      console.log('Login form submitted:', this.loginForm)
      // 示例：清空表单
      this.loginForm.email = ''
      this.loginForm.password = ''
    },
    handleRegister() {
      // 这里添加注册逻辑，例如调用 API
      console.log('Register form submitted:', this.registerForm)
      // 示例：清空表单
      this.registerForm.name = ''
      this.registerForm.email = ''
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
