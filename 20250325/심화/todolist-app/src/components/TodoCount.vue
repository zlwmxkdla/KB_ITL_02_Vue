<!-- vueinit : vue3 자동 완성 -->

<template>
  <div class="row mb-3">
    <div class="col-md text-center">
      전체 todo 개수 : <span>{{ todolist.length }}</span>
    </div>
    <div class="col-md text-center">
      <!-- 완료 todo 개수 : <span :class="completedCount && completed">{{completedCount}}</span> -->
      완료 todo 개수 :
      <span :class="{ completed: completedCount > 0 }">{{
        completedCount
      }}</span>
    </div>
    <div class="col-md text-center">
      미완료 todo 개수 :
      <span :class="{ notCompleted: todolist.length - completedCount > 0 }">{{
        todolist.length - completedCount
      }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TodoCount',
  //props는 부모로부터 데이터 전달받기 + 유효성 검사 진행
  props: {
    todolist: {
      type: Array,
      required: true,
    },
  },
  computed: {
    // 완료 개수 카운트
    completedCount() {
      // todolist의 요소 중 completed 가 true인 요소만 남긴 배열 반환
      return this.todolist.filter((todo) => todo.completed).length;
    },
  },
};
</script>
