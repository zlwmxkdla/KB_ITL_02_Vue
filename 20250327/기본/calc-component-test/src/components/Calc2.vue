<!-- Composition API 적용 -->

<template>
  <div>
    X : <input type="text" v-model.number="x" /><br />
    Y : <input type="text" v-model.number="y" /><br />

    <button @click="caculateSum(x, y)">계산하기</button>
    <p>결과 : {{ sum1 }}</p>
  </div>
</template>
<script>
import { ref } from 'vue';
export default {
  name: 'Calc2',

  setup() {
    // 계산 관련 data, method
    const x = ref(5);
    const y = ref(7);
    const sum = ref(12);

    // -------------------------------------------------------

    const caculateSum = (num1, num2) => {
      sum1.value = num1 + num2;
    };
    //setup() return 구문에 작성 - > template에서 사용 가능해짐
    return { x, y, sum1, caculateSum };
  },
};
</script>
<style></style>
