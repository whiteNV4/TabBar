<!--  -->
<template>
  <div id="tab-bar">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "TarBar",
};
</script>

<style scoped>
#tab-bar {
  display: flex;
  background-color: #f6f6f6;

  /* 位置 */
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  box-shadow: 0px -3px 1px rbga(100, 100, 100, 0.8);
}
</style>
