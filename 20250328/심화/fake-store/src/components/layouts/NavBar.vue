<template>
  <nav class="navbar navbar-expand-md bg-dark navbar-dark mt-2">
    <span class="navbar-brand"></span>
    <button class="navbar-toggler" type="button" @click="changeIsNavShow">
      <span class="navbar-toggler-icon"></span>
    </button>

    <div :class="navClass">
      <ul class="navbar-nav">
        <li class="nav-item">
          <router-link class="nav-link" to="/">Fake Store</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="/electronics">가전</router-link>
        </li>
        <li class="nav-item">
          <RouterLink class="nav-link" to="/jewelery">주얼리</RouterLink>
        </li>
        <li class="nav-item">
          <RouterLink class="nav-link" to="/mensclothing">남성의류</RouterLink>
        </li>
        <li class="nav-item">
          <RouterLink class="nav-link" to="/womenclothing">여성의류</RouterLink>
        </li>
      </ul>
    </div>
  </nav>
</template>
<script>
import { reactive, computed } from 'vue';

export default {
  setup() {
    const state = reactive({ isNavShow: false });
    const navClass = computed(() =>
      state.isNavShow
        ? 'collapse navbar-collapse show'
        : 'collapse navbar-collapse'
    );
    const changeIsNavShow = () => {
      state.isNavShow = !state.isNavShow;
    };
    return { state, changeIsNavShow, navClass };
  },
};
</script>
