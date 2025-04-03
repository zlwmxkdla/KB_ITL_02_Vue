<!-- NavItem 컴포넌트 -->
<template>
  <li class="nav-item">
    <RouterLink :to="props.menu.uri" class="nav-link">{{
      props.menu.text
    }}</RouterLink>
  </li>
</template>

<script setup>
const props = defineProps({
  menu: { type: Object, required: true },
});
</script>
