<!-- vueinit : vue3 자동 완성 -->

<template>
  <li
    :key="todoItem.id"
    class="list-group-item"
    :class="{ 'list-group-item-success': todoItem.completed }"
  >
    <input
      type="checkbox"
      class="pointer me-3"
      v-model="todoItem.completed"
      @click="toggleCompletedHandler(todoItem.id)"
    />

    <span class="pointer" :class="{ 'todo-done': todoItem.completed }">
      {{ todoItem.todo }} {{ todoItem.completed ? '(완료)' : '' }}
    </span>

    <span
      class="float-end badge bg-secondary pointer"
      @click.stop="emit('delete-todo', todoItem.id)"
      >삭제</span
    >
  </li>
</template>

<script setup>
const props = defineProps({
  todoItem: {
    type: Object, //객체 타입 검사
    required: true, //필수 데이터
  },
});

const toggleCompletedHandler = (id) => {
  //emit() : 이벤트 발신 시 사용하는 함수 (템플릿에서는 $emit 사용 가능 )
  emit('toggle-completed', id);
};
//defineEmits : 자식에서 부모로 이벤트 발신 정의
const emit = defineEmits(['toggle-completed', 'delete-todo']);
</script>
