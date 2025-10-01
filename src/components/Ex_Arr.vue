<template>
  <div>
    <h1>배열 조작 예제</h1>
    <p>현재 배열 : {{ items }}</p>
    <div class="btn-wrap">
      <button @click="addItem">push() - 배열에 추가</button>
      <button @click="removeLastItem">pop() - 마지막을 제거하는 메서드</button>
      <button @click="removeFirstItem">shift() - 첫번째 내용 제거하는 메서드</button>
      <button @click="removeAndItem">unshift() - 첫번째 내용 추가하는 메서드</button>
      <button @click="removeAndAddItem">splice() - 요소 변경</button>
      <button @click="sortItems">sort() - 정렬</button>
      <button @click="reverseItems">reverse() - 역순정렬</button>
      <button @click="filterItems">filter() - "a" 포함된 요소만 필터링</button>
      <button @click="concatItems">concat() - 새로운 배열과 결합</button>
      <button @click="sliceItems">slice() - 인덱스 1~2 요소 추출</button>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
const items = ref(["Apple", "Banana", "Cherry", "Orange", "Grapes"]);
// push()
const addItem = () => {
  items.value.push("pineapple"); // 중복 추가 가능
};
const removeLastItem = () => {
  items.value.pop(); //배열의 마지막 내용을 제거하는 기능 (중복 제거 가능)
};
// shift()
const removeFirstItem = () => {
  items.value.shift();
};
// unshift()
const removeAndItem = () => {
  items.value.unshift("Melon");
};
// splice()
const removeAndAddItem = () => {
  items.value.splice(1, 1, "kiwi"); //splice(index,delete갯수,추가아이템) 순
};
// sort()
const sortItems = () => {
  items.value.sort(); //알파벳 순으로 정렬 변경하기
};
// reverse()
const reverseItems = () => {
  items.value.reverse(); //원래 순의 반대로 정렬
};
// filter() - a포함된 배열만 표시
const filterItems = () => {
  items.value = items.value.filter((item) => {
    // console.log(item);
    return item.includes("a"); //includes() = 있는지 없는지 확인하는 메서드 (소문자 a가 포함된 단어만 표시)
  });
};
// concat()
const concatItems = () => {
  items.value = items.value.concat(["strawberry", "blueberry"]);
};
// slice() - start 부터 and 전까지 잘려 출력된다.
// 1부터 3전까지 잘려 나온다.
//이해 보충 필요
const sliceItems = () => {
  items.value = items.value.slice(1, 3); //남길 배열 지정 (시작, 끝)
};
</script>
<style scoped></style>
