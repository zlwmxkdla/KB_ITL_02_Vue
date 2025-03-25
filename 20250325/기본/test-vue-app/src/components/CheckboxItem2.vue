<template>
  <div>
    <li><input type="checkbox" :checked="idol.checked" />{{ idol.name }}</li>
  </div>
</template>
<script>
export default {
  name: 'CheckedboxItem2',
  props: ['idol'],
};
</script>
<style></style>
