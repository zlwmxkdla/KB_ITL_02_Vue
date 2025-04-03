<template>콘솔에 출력합니다.</template>
<script setup>
import axios from 'axios';
const listURL = 'http://localhost:3000/todos';
const todoURL = (id) => `http://localhost:3000/todos/${id}`;

const requestAPI = () => {
  let todoList = [];
  axios
    .get(listURL)
    .then((response) => {
      todoList = response.data;
      console.log('# TodoList :', todoList);
      return todoList[0].id;
    })
    .then((id) => {
      return axios.get(todoURL(id));
    })
    .then((response) => {
      console.log('#ID가 1인 Todo:', response.data);
    })
    .catch((error) => {
      console.error('에러 발생:', error);
    });
};

requestAPI();
</script>
