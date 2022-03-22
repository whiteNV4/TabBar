<!--  -->
<template>
  <div class="tab-bar-item" @click="itemClick">
    <div v-if="!isActive">
      <slot name="item-icon"></slot>
    </div>
    <div v-else="isActive">
      <slot name="item-icon-active"></slot>
    </div>
    <div :style="activeStyle">
      <slot name="item-text"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "TabBarItem",
  props: {
    path: String,
    activeColor: {
      type: String,
      default: "green",
    },
  },
  data() {
    return {
      // isActive: false,
    };
  },
  methods: {
    itemClick() {
      this.$router.replace(this.path);
    },
  },
  computed: {
    isActive() {
      //  /home -> item1(/home) = true
      //  /home -> item1(/category) = true
      //  /home -> item1(/cart) = true
      //  /home -> item1(/profile) = true
      //颜色的动态控制
      return this.$route.path.indexOf(this.path) !== -1;
    },
    //下列代码直接放到style中过于复杂，因此放到computed或methods中
    activeStyle() {
      return this.isActive ? { color: this.activeColor } : {};
    },
  },
};
</script>

<style scoped>
.tab-bar-item {
  flex: 1;
  text-align: center;
  height: 49px;
  font-size: 14px;
}
.tab-bar-item img {
  width: 24px;
  height: 24px;
  margin-top: 3px;
  /* 去除图像下多的3px像素 */
  vertical-align: middle;
  margin-bottom: 2px;
}
</style>
