# Quasar To-Do List

這是一個使用 Quasar Framework 和 Vue.js 構建的簡單待辦事項清單應用。

## 功能

- 新增待辦事項
- 標記待辦事項為已完成
- 刪除待辦事項
- 響應式設計，適合桌面和手機

## 主要組件

應用程式的主要組件是 `Todo.vue`，它包含以下功能：

1. 待辦事項列表管理
2. 新增待辦事項
3. 完成待辦事項
4. 刪除待辦事項

## 如何運行

1. 安裝依賴：

```bash
pnpm install
```

2. 啟動開發服務器：

```bash
pnpm run dev
```

## 項目結構

- `<script setup>`: 包含 Vue 3 Composition API 的邏輯
- `<template>`: 定義 UI 結構，使用 Quasar 組件

## 主要功能說明

1. `addTodo()`: 新增待辦事項到列表
2. `removeToDo(itemId)`: 從列表中刪除指定的待辦事項
3. `finishToDo(itemId)`: 切換待辦事項的完成狀態

## UI 組件

- `q-layout`: 定義整體頁面布局
- `q-header`: 頁面頂部的標題欄
- `q-footer`: 頁面底部的頁腳
- `q-card`: 包含待辦事項列表的卡片
- `q-input`: 用於輸入新的待辦事項
- `q-btn`: 用於各種操作的按鈕

## 注意事項

- 新增的待辦事項最多只能包含 7 個字符
- 使用 `text-strike`  class 來標記已完成的待辦事項

## 參考資料

[Vite plugin for Quasar](https://quasar.dev/start/vite-plugin)
