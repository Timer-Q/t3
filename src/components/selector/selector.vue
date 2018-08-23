<template>
  <div class="selector">
    <input :value='value' type="text" class="selector-input" />
    <ul class="selector-list">
      <li class="selector-list-item">123</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      value: '123',
    };
  },
  mounted() {
    const query = wx.createSelectorQuery();
    query.select('.selector').boundingClientRect();
    query.exec((res) => {
      console.log(res);
    });
  },
};
</script>

<style lang="scss" scoped>
.selector {
  position: relative;
  &-input {
    border: 1px solid #ddd;
    outline: none;
  }
  &-list {
    list-style: none;
    position: absolute;
    top: 100%;
    left: 0;
  }
}
</style>
