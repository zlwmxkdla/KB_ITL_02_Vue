<template>
  <div class="card card-body">
    <h2>About</h2>
    <p>요청 경로 : {{ $route.fullPath }}</p>
  </div>
</template>


 <!-- 기본

// export default{
//     name:'About',
//     created(){
//         console.log(this.$route);
//     },
// };


 setup 함수로 재정의

// import { useRoute } from 'vue-router';
// export default {
//   name: 'About',
//   setup() {
//     const route = useRoute();
//     console.log(route);
//     return {};
//   },
// }; -->


// Composition API 방식

<script setup>
import { useRoute } from 'vue-router';

const route=useRoute;
console.log(route);
</script>
    
