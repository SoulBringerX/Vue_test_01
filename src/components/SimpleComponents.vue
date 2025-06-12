<template>
  <div class="simple-component">
    <h2>{{ greeting }}</h2>
    <button @click="changeGreeting">Change Greeting</button>
    <button @click="fetchData">Fetch Data from Backend</button>
    <p v-if="backendData">{{ backendData }}</p>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'SimpleComponent',
  setup() {
    // 定义一个响应式变量
    const greeting = ref('Hello from SimpleComponent')
    // 定义一个变量来存储后端返回的数据
    const backendData = ref<string | null>(null)

    // 定义一个方法来改变问候语
    const changeGreeting = () => {
      greeting.value = 'Greetings changed! Click again to reset.'
    }

    // 定义一个方法来调用后端服务
    const fetchData = async () => {
      try {
        const response = await fetch('http://localhost:9001/consumer')
        if (!response.ok) {
          throw new Error('Network response was not ok')
        }
        const data = await response.text()
        backendData.value = data
      } catch (error) {
        console.error('Error fetching data:', error)
        backendData.value = 'Failed to fetch data'
      }
    }

    return {
      greeting,
      backendData,
      changeGreeting,
      fetchData,
    }
  },
})
</script>

<style scoped>
.simple-component {
  padding: 20px;
  margin: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
}
button {
  padding: 5px 10px;
  margin-top: 10px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
button:hover {
  background-color: #45a049;
}
</style>
