<script setup>
import { computed, ref } from 'vue'

const newTodo = ref('')
const todos = ref([
  { id: 1, text: '学习 Vue 3 组合式 API', done: true },
  { id: 2, text: '用 Vite 启动开发服务器', done: false }
])

let nextId = 3

const remaining = computed(() => todos.value.filter((todo) => !todo.done).length)

function addTodo() {
  const text = newTodo.value.trim()
  if (!text) return
  todos.value.push({ id: nextId++, text, done: false })
  newTodo.value = ''
}

function removeTodo(id) {
  todos.value = todos.value.filter((todo) => todo.id !== id)
}

function clearDone() {
  todos.value = todos.value.filter((todo) => !todo.done)
}
</script>

<template>
  <main class="card">
    <h1>简易待办清单</h1>
    <p class="subtitle">Vue 3 + Vite 示例项目</p>

    <form class="add-form" @submit.prevent="addTodo">
      <input v-model="newTodo" type="text" placeholder="输入待办事项…" />
      <button type="submit">添加</button>
    </form>

    <ul class="todo-list">
      <li v-for="todo in todos" :key="todo.id" :class="{ done: todo.done }">
        <label>
          <input v-model="todo.done" type="checkbox" />
          <span>{{ todo.text }}</span>
        </label>
        <button class="remove" type="button" @click="removeTodo(todo.id)">删除</button>
      </li>
      <li v-if="todos.length === 0" class="empty">暂无待办，先添加一条吧</li>
    </ul>

    <footer class="toolbar">
      <span>剩余 {{ remaining }} 项</span>
      <button type="button" :disabled="!todos.some((todo) => todo.done)" @click="clearDone">
        清除已完成
      </button>
    </footer>
  </main>
</template>
