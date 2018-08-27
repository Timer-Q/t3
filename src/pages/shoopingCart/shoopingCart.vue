<template>
  <div class="cart">{{msg}}</div>
</template>

<script>
export default {
  data() {
    return {
      msg: 'shooping cart',
    };
  },
};
</script>

<style lang="scss" scoped>
@import "../../styles/color.scss";

.cart {
  background-color: $purple;
  
}
</style>

