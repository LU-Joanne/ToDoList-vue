<script setup>
import { ref } from 'vue';

const text = ref('')
const todos = ref([])
// const isEditing = ref(false);
const editingTodo = ref('');
let beforeText = '';

const addTodo = () => {
  if (text.value.trim()) {
    todos.value.push({ text: text.value, completed: false });
    text.value = '';
  }
};

const editText = (todo) => {
  beforeText = todo.text;
  editingTodo.value = todo;

}

const removeTodo = (index) => {
  todos.value.splice(index, 1);
}

const saveEdit = (todo) => {
  todo.text = todo.text.trim();
  if (todo.text === '') {
    todo.text = beforeText;
    window.alert('請輸入有效內容')
  }
  editingTodo.value = null;
}

const cancelEdit = (todo) => {
  editingTodo.value = null;
  todo.text = beforeText;
}

</script>

<template>
  <div class="todo-list">
    <div class="header">
      <h1>TODOLIST</h1>
      <input v-model="text" @keyup.enter="addTodo" placeholder="添加新事項">
      <button class="add" @click="addTodo">添加</button>
    </div>
    <ul>
      <li v-for="(todo, index) in todos" :key="index" :class="{ editing: todo === editingTodo }">
        <input class="box" type="checkbox" v-model="todo.completed" />
        <div v-if="editingTodo === todo">
          <input v-model="todo.text" @keyup.enter="saveEdit(todo)" @blur="cancelEdit" />
          <button @click="saveEdit(todo)">儲存</button>
          <button @click="cancelEdit(todo)">取消</button>
        </div>
        <div class="todo-box" v-else>
          <span :class="{ completed: todo.completed }" @dblclick="editText(todo)">{{
            todo.text }}</span>
          <button class="remove" @click="removeTodo(index)">X</button>
        </div>

      </li>
    </ul>
  </div>
</template>
<style>
.todo-list {
  width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}

.header {
  text-align: center;
}

h1 {
  font-weight: 700;
}

button {
  margin-left: 10px;
  border: none;
  border-radius: 4px;
  padding: 5px 10px;
  cursor: pointer;
}

button.add {
  color: white;
  background-color: #FF5722;
}

button.remove {
  background-color: transparent;
}

li {
  list-style-type: none;
  display: grid;
  padding: 5px 0;
  border-bottom: 1px solid #e7e7e7;
  grid-template-columns: 0fr 1fr;
}

input.box {
  margin-right: 15px;
}

input[type="checkbox"] {
  accent-color: #FF5722;
}

.completed {
  text-decoration: line-through;
  color: #b2b2b2;
}

.todo-box {
  display: flex;
  justify-content: space-between;
  padding: 0px 10px;
}
</style>
