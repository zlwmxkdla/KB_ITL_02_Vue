<template>콘솔에 출력합니다.</template>
<script setup>
import axios from 'axios';
const listURL = 'http://localhost:3000/todos';
const todoURL = (id) => `http://localhost:3000/todos/${id}`;

const requestAPI = async () => {
  let todoList;
  let response = await axios.get(listURL);
  todoList = response.data;
  console.log('#TodoList : ', todoList);
  for (let i = 0; i < todoList.length; i++) {
    response = await axios.get(todoURL + todoList[i].id);
    console.log(`# ${i + 1}번 째 Todo:`, response.data);
  }
};

requestAPI();
</script>
