<!-- vueinit : vue3 자동 완성 -->

<template>
  <div id="app" class="container">
    <div class="card card-body bg-light">
      <div class="title">🕒 TodoList App 💻</div>
    </div>

    <div class="card card-default card-borderless">
      <div class="card-body">
        <!-- 입력용 컴포넌트 
         방출(add-todo)된 이벤트가 감지되었을 때
         addTodo()메서드 호출
        -->
        <InputTodo @add-todo="addTodo" />

        <!-- 카운트 컴포넌트 -->
        <TodoCount v-bind:todoList="state.todoList" />
        <!-- 목록 컴포넌트 
            - 목록 화면 렌더링에 필요한 데이터
            - todoList를 부모인 App.vue가 가지고 있음
            -> 부모 ->자식으로 데이터 전달하는 props 이용해야 함
            - (v-bind: 전달할 이름="데이터") 이용해서 한다. 
        -->
        <TodoList
          v-bind:todoList="sortedList"
          @toggle-completed="toggleCompleted"
          @delete-todo="deleteTodo"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive, onMounted, computed } from 'vue'; //onmounted는 브라우저에 출력된 직후 수행되는 콜백 등록 가능
import InputTodo from './components/InputTodo.vue'; //지역 컴포넌트 등록
import TodoList from './components/TodoList.vue';
import TodoCount from './components/TodoCount.vue';

const state = reactive({ todoList: [] });
onMounted(() => {
  state.todoList.push({
    id: Date.now(),
    todo: '자전거 타기',
    completed: false,
  });
  state.todoList.push({
    id: Date.now() + 1,
    todo: '딸과 공원 산책',
    completed: true,
  });
  state.todoList.push({
    id: Date.now() + 2,
    todo: '일요일 애견 카페',
    completed: false,
  });
  state.todoList.push({
    id: Date.now() + 3,
    todo: 'Vue 원고 집필',
    completed: false,
  });
});

// 할 일 추가 메서드
// receiveTdo : InputTodo 컴포넌트의
// this.$emit('add-todo', this.todo); 에서 전달된 this.todo(payload)
const addTodo = (receiveTodo) => {
  state.todoList.push({
    id: Date.now(),
    todo: receiveTodo,
    completed: false,
  });
};

// 할 일 완료 여부 변경 메서드
// 매개변수 id : TodoListItem에서부터 전달된 id
const toggleCompleted = (id) => {
  let index = state.todoList.findIndex((item) => id === item.id);
  state.todoList[index].completed = !state.todoList[index].completed;
};

const deleteTodo = (id) => {
  // 배열.findIndex(콜백함수) : 콜백 함수의 결과가 true인 index를 반환
  let index = state.todoList.findIndex((item) => id === item.id);
  state.todoList.splice(index, 1);
};

// computed : data가 변할 때 자동으로 계산
// -> 계산되서 return된 값은 함수명(sortedList)으로 사용

const sortedList = computed(() => {
  state.todoList.sort((t1, t2) => {
    // true > false  -> 결과 : true
    if (t1.completed > t2.completed) {
      return 1; // 양수 반환 시 자리 바뀜 (t1, t2 -> t2, t1)
    }

    if (t1.completed < t2.completed) {
      return -1; // 음수 반환 시 자리 바꿈 X
    }

    // 위 if문 실행 X === completed가 같을 경우
    // -> 문자열 오름 차순 정렬

    // 모두 소문자로 변경(대소문자 구분 X)
    const todo1 = t1.todo.toLowerCase();
    const todo2 = t2.todo.toLowerCase();

    if (todo1 > todo2) return 1; // 자리 교체
    else if (todo1 === todo2) return 0; // 유지
    else return -1; // 유지
  });

  // 정렬된 todoList 반환
  return state.todoList;
});
</script>
