<!-- Composition API 적용 -->

<template>
  <div>
    <h3>Options API</h3>
    <input
      type="text"
      placeholder="입력하면 대문자로 변환"
      :value="name"
      @input="changeName($event.target.value)"
    />
  </div>

  <div>
    X : <input type="text" v-model.number="x" /><br />
    Y : <input type="text" v-model.number="y" /><br />

    <button @click="caculateSum(x, y)">계산하기</button>
    <p>X + Y = {{ sum1 }}</p>
  </div>
</template>
<script>
import { ref } from 'vue';
export default {
  name: 'Calc2',

  setup() {
    // name 관련 data, method
    const name = ref(''); //data 대체 , 값 접근 시 .value 이용
    const changeName = (inputName) => {
      name.value = inputName.toUpperCase();
    };

    // 계산 관련 data, method
    const x = ref(5);
    const y = ref(7);
    const sum = ref(12);

    // -------------------------------------------------------

    const caculateSum = (num1, num2) => {
      sum1.value = num1 + num2;
    };
    //setup() return 구문에 작성 - > template에서 사용 가능해짐
    return { name, changeName, x, y, sum1, caculateSum };
  },
};
</script>
<style></style>
