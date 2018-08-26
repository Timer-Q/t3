<template>
  <div class="navigator">
    <div
      v-for="(item, index) in navInfo"
      :class="['navigator-item', item.classes, {'is-actived': activeIndex > index}, {'is-activation': activeIndex === index}]"
      :key="index">
      <p class="navigator-item-title">{{item.title}}</p>
      <p class="navigator-item-header">{{item.header}}</p>
      <p class="navigator-item-triangle"></p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      navInfo: [
        {
          title: 'step1:',
          header: '选酒店',
        },
        {
          title: 'step2:',
          header: '选航班',
          classes: 'light-gray',
        },
        {
          title: 'step3:',
          header: '选最佳组合优惠',
          classes: 'navigator-item-half gray',
        },
      ],
    };
  },
  props: {
    activeIndex: {
      type: [Number, String],
      default: 1,
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../../styles/color.scss";
$nav-height: 110rpx;

.navigator {
  display: flex;
  position: fixed;
  top: 0;
  left: 0;
  align-items: center;
  width: 100%;
  height: $nav-height;
  &-item {
    position: relative;
    height: 100%;
    flex: 1;
    padding-top: 20rpx;
    padding-bottom: 20rpx;
    padding-left: 20rpx;
    background-color: $black-68;
    box-sizing: border-box;
    &:not(:first-child) {
      padding-left: $nav-height / 2 + 20;
    }
    &-triangle {
      display: inline-block;
      position: absolute;
      top: 0;
      left: 100%;
      z-index: 1;
      width: 0;
      height: 0;
      border-color: transparent;
      border-left-color: $black-68;
      border-width: $nav-height / 2 $nav-height / 4 $nav-height / 2 $nav-height /
        4;
      border-style: solid;
    }
    &.light-gray {
      background-color: $black-e0;
      .navigator-item-triangle {
        border-left-color: $black-e0;
      }
    }
    &.gray {
      background-color: $black-cb;
      .navigator-item-triangle {
        border-left-color: $black-cb;
      }
    }
    &.is-activation {
      background-color: $yellow;
      .navigator-item-triangle {
        border-left-color: $yellow;
      }
    }
    &.is-actived {
      z-index: 2;
      background-color: $yellow;
      opacity: 0.6;
      .navigator-item-triangle {
        border-left-color: $yellow-light;
      }
    }
    &-title {
      font-size: 24rpx;
    }
    &-header {
      font-size: 32rpx;
    }
    &.navigator-item-half {
      flex: 2;
    }
  }
}
</style>

