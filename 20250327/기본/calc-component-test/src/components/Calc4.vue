<!-- Composition API 적용 -->

<template>
  <div>
    X : <input type="text" v-model.number="state.x" /><br />
    Y : <input type="text" v-model.number="state.y" /><br />

    <p>결과 : {{ result }}</p>
  </div>
</template>
<script>
import { reactive, computed } from 'vue';
export default {
  name: 'Calc4',
  setup() {
    const state = reactive({ x: 10, y: 20 });
    const result = computed(() => {
      return state.x + state.y;
    });

    //setup() return 구문에 작성 - > template에서 사용 가능해짐
    return { state, result };
  },
};
</script>
<style></style>
