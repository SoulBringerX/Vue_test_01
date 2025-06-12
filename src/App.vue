<template>
  <div id="app">
    <header>
      <h1>WelCome!</h1>
    </header>
    <main>
      <LoginPage />
    </main>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import LoginPage from './components/LoginPage.vue'

export default defineComponent({
  components: {
    LoginPage,
  },
})
</script>

<style>
/* 全局样式 */
body,
html {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  font-family: Arial, sans-serif;
  background-color: #f0f2f5;
  display: flex;
  flex-direction: column;
}

#app {
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100%;
}

/* header 样式 */
header {
  background-color: #42b983;
  color: white;
  text-align: center;
  padding: 1rem 0;
  flex-shrink: 0; /* 防止 header 被挤压 */
}

/* main 样式 */
main {
  flex-grow: 1; /* 占满剩余空间 */
  display: flex;
  justify-content: center; /* 水平居中 */
  align-items: center; /* 垂直居中 */
  padding: 20px;
}

/* 登录页面的样式 */
.login-container {
  max-width: 400px;
  width: 100%;
  padding: 20px;
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  text-align: center; /* 确保标题居中 */
}
</style>
