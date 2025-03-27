<template>
  <div>
    <InputName v-model:name="searchName" />
    <h3>검색어 : {{ searchName }}</h3>
  </div>

  <hr />
  <h1>부모 Click Count : {{ count }}</h1>

  <!-- 자식 Click Count -->
  <ClickCount />

  <h1>Teleport Test</h1>
  <button @click="changeModal">isModal 상태 변경</button>
  <!-- id="modal" 요소에 모달 컴포넌트 렌더링 -->
  <teleport to="#modal">
    <Modal v-if="isModal" />
  </teleport>
</template>

<script>
import InputName from './components/InputName.vue';
import ClickCount from './components/ClickCount.vue';
import { computed } from 'vue';

//텔레포트 테스트
import Modal from './components/Modal.vue';

export default {
  name: 'App',
  components: { InputName, ClickCount, Modal },
  data() {
    return { searchName: 'John', count: 0, isModal: false };
  },

  methods: {
    changeModal() {
      this.isModal = true;
      setTimeout(() => {
        this.isModal = false;
      }, 2000);
    },

    //하위 컴포넌트에게 정보 제공
    provide() {
      return {
        //count 변경 시 하위 컴포넌트 재랜더링
        cnt: computed(() => this.count),

        //increment()호출시 App.vue의 count 1 증가
        increment: () => this.count++,
      };
    },
  },
};
</script>
