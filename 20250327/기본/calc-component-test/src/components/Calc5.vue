<!-- Composition API 적용 -->

<template>
  <div>
    X : <input type="text" v-model.number="x" /><br />

    <p>결과 : {{ result }}</p>
  </div>
</template>
<script>
import { ref, watch } from 'vue';
export default {
  name: 'Calc5',
  setup() {
    const x = ref(0);
    const result = ref(0);
    watch(x, (current, old) => {
      console.log(`${old} -> ${current}`);
      result.value = current * 2;
    });

    //setup() return 구문에 작성 - > template에서 사용 가능해짐
    return { x, result };
  },
};
</script>
<style></style>
