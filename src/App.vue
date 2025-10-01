<template>
  <div class="container">
    <Event />
    <FormEx />
  </div>
  <h2>Array</h2>
  <div class="container">
    <div class="contents">
      <button @click="showArr = !showArr">{{ showArr ? "닫기" : "배열예제보기" }}</button>
      <Ex_Arr v-if="showArr"/>
    </div>
    <div class="contents">
      <button @click="showTodoList = !showTodoList">{{ showTodoList ? "닫기" : "목록 보기" }}</button>
      <Todolist v-if="showTodoList"/>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
import Event from "./components/Event.vue";
import FormEx from "./components/Form-ex.vue";
import Ex_Arr from "./components/Ex_Arr.vue";
import Todolist from "./components/Todolist.vue";
const showArr = ref(false)
const showTodoList = ref(false)
</script>
<style scoped>
.container {
  display: flex;
  gap: 20px;
}
.container div {
  flex: 1;
  background-color: antiquewhite;
}
</style>
