<!-- vueinit : vue3 자동 완성 -->

<template>
  <div class="row">
    <div class="col">
      <ul class="list-group">
        <!-- 할 일 목록 요소 컴포넌트 추가 -->

        <!-- props로 받은 데이터 수정하면 안 됨
         =>emit을 이용해서 부모로 전달하여 수정
         
         TodoItem -> TodoList -> App 
         -->
        <TodoListItem
          v-for="todo in todolist"
          :todoitem="todo"
          @toggle-completed="$emit('toggle-completed', $event)"
          @delete-todo="$emit('delete-todo', $event)"
        />
        <!-- 
        $event : 자식 컴포넌트에서 방출된 payload를 참조하는 변수(id)
        
        -->
      </ul>
    </div>
  </div>
</template>

<script>
import TodoListItem from './TodoListItem.vue';

export default {
  name: 'TodoList',

  //자식 컴포넌트 등록
  components: { TodoListItem },

  //부모로부터 전달받은 데이터 수신 + 유효성 검사
  props: {
    //전달받은 todolist 는 배열 형태, 필수 데이터이어야 함 비어있으면 안 됨
    todolist: { type: Array, required: true },
  },

  //부모 컴포넌트로 방출되는 이벤트 검사
  emit: ['toggle-completed', 'delete-todo'],
};
</script>
