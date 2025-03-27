<!-- Composition API 적용 -->

<template>
  <div>
    X : <input type="text" v-model.number="state.x" /><br />
    Y : <input type="text" v-model.number="state.y" /><br />

    <button @click="calcAdd(x, y)">계산</button>
    <p>결과 : {{ state.result }}</p>
  </div>
</template>
<script>
import { reactive } from 'vue';
export default {
  name: 'Calc3',
  setup() {
    const state = reactive({ x: 10, y: 20, result: 30 });
    const calcAdd = () => {
      state.result = state.x + state.y;
    };
    //setup() return 구문에 작성 - > template에서 사용 가능해짐
    return { state, calcAdd };
  },
};
</script>
<style></style>
