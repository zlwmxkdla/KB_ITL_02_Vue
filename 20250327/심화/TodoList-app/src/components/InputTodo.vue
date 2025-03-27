<!-- vueinit : vue3 자동 완성 -->

<template>
  <div class="row mb-3">
    <div class="col">
      <div class="input-group">
        <input
          id="msg"
          type="text"
          class="form-control"
          name="msg"
          placeholder="할일을 여기에 입력!"
          v-model.trim="todo"
          @keyup.enter="addTodoHandler"
        />

        <!-- 추가 버튼 클릭 시 작성된 할 일 내용을 todoList에 추가 -->
        <span class="btn btn-primary input-group-addon" @click="addTodoHandler"
          >추가</span
        >
      </div>
    </div>
  </div>
</template>

<script setup>
//ref()에 등록된 값 접근 방법 : 변수명.value
import { ref } from 'vue';
const todo = ref(''); //todo가 ref 로 묶으면 객체가 됨

//부모로 방출할 이벤트 유효성 검사
const emit = defineEmits(['add-todo']);
const addTodoHandler = () => {
  if (todo.value.length >= 3) {
    //작성된 할 일(this.todo)을
    //부모 컴포넌트(App.vue)로 전달하기!
    //-> 이벤트 발신(emit) 이용

    //$emit(이벤트명, 페이로드): 이벤트 발신 메서드
    emit('add-todo', todo.value);
    todo.value = ''; //입력된 내용 삭제
  } else {
    alert('할 일은 3글자 이상으로 작성해주세요!!');
  }
};
</script>
