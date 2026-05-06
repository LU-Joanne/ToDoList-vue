# ToDoList-vue

此專案使用Vue 3 (Composition API)開發的 To-Do List。除了增刪功能外，還有雙擊編輯儲存與取消，模擬真實應用中的互動體驗。

## 功能
- 新增事項：輸入文字並按 Enter 或點擊按鈕即可加入清單。
- 完成標註：點擊勾選框可標記事項為已完成，文字會自動加上刪除線。
- 雙擊修改 (Double Click Edit)：在事項文字上點擊兩下即可進入編輯模式。
- 刪除事項：一鍵刪除不再需要的項目。

## 專案技術
- Vue v3.5.22
- Vite v7.1.7
- Node.js v22.14.0

## 資料夾說明
- src
  - components 元件放置處
  - assets 靜態檔案放置處

## 在 Local 端的安裝＆運行步驟
Node.js 建議為LTS 版本
### 取得專案 (Clone)
```sh
git clone https://lu-joanne.github.io/ToDoList-vue/
```
### 移動到專案內
```sh
cd ToDoList-vue
```
### 安裝套件 (Install Dependencies)
```sh
npm install
```
### 啟動開發伺服器 (Run for Development)
```sh
npm run dev
```
### 編譯與打包 (Build for Production)
```sh
npm run build
```
