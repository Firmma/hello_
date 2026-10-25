# vue-simple-app

一个简易的 Vue 3 + Vite 待办清单示例项目。

## 快速开始

```bash
npm install
npm run dev      # 开发服务器 http://localhost:5173
npm run build    # 生产构建，输出到 dist/
npm run preview  # 预览构建产物
```

## 目录结构

```
index.html          # 入口 HTML
vite.config.js      # Vite 配置
src/main.js         # 应用入口
src/App.vue         # 待办清单页面（组合式 API）
src/style.css       # 全局样式
```

## 功能

- 添加待办、勾选完成、删除单条、清除已完成
- 实时统计剩余未完成数量
