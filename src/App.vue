<template>
  <div id="app">
    <header>
      <h1><img src="./assets/logo.svg" /></h1>
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
    LoginPage, // 注册 LoginPage 组件
  },
})
</script>

<style>
/* 全局样式 */
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f0f2f5;
}

/* header 样式 */
header {
  background-color: #42b983;
  color: white;
  text-align: center;
  padding: 1rem 0;
}

/* main 样式 */
main {
  padding: 20px;
}
</style>
