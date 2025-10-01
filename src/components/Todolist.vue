<template>
  <div class="todo-wrap">
    <h1>To-do</h1>
    <!-- 할일 입력 -->
    <div class="input-group">
      <input type="text" v-model="newTodo" placeholder="새로운 할 일 목록 입력." />
      <button @click="addTodo">추가</button>
    </div>
    <h2>📌진행 중</h2>
    <ul v-for="todo in todos" :key="todo.id">
      <!-- key는 고유한 것을 넣는것을 추천 -->
      <li v-if="!todo.isComplete"><input type="checkbox" @change="toggleComplete(todo)" />{{ todo.name }}</li>
    </ul>
    <!-- 완료된 할 일 목록 -->
    <h2>✅완료</h2>
    <ul v-for="todo in todos" :key="todo.id">
      <!-- key는 고유한 것을 넣는것을 추천 -->
      <li v-if="todo.isComplete">
        <input type="checkbox" checked @change="toggleComplete(todo)" />
        <del>{{ todo.name }}</del>
      </li>
    </ul>
    <!-- 완료된 목록 삭제 버튼 -->
    <button class="delet-btn" @click="deleteCompleted">완료된 할 일 삭제</button>
  </div>
</template>
<script setup>
import { ref } from "vue";

// 할일 목록 데이터
const todos = ref([
  { id: 1, name: "Vue 공부하기", isComplete: false },
  { id: 2, name: "운동하기", isComplete: true },
  { id: 3, name: "책 읽기", isComplete: false },
]);
// 할 일 추가
const newTodo = ref("");
const addTodo = () => {
  if (newTodo.value.trim()) {
    todos.value.push({ id: Date.now(), name: newTodo.value, isComplete: false });
    newTodo.value = ""; //입력필드 초기화
  } else {
    return alert("할 일을 작성하세요");
  }
};
// 할 일 완료 / 미 완료 토글
const toggleComplete = (todo) => {
  // console.log(todo);
  todo.isComplete = !todo.isComplete;
};
// 완료된 항목 삭제 기능
const deleteCompleted = () => {
  todos.value = todos.value.filter((todo) => !todo.isComplete);
};
</script>
<style scoped></style>
