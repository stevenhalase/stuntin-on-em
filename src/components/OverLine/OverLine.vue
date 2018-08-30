<template>
  <div :class="classes" :style="`--propColor: ${color};`">
    <slot></slot>
  </div>
</template>

<script>
/**
 * OverLine component
 */
export default {
  name: 'OverLine',
  props: {
    /**
    * Color of OverLine
    * `Hex value '#fac312'`
    */
    color: {
      type: String,
      default: '#fac312',
    },
    /**
    * Underline toggle
    * `true, false`
    */
    underline: {
      type: Boolean,
    },
  },
  computed: {
    classes() {
      let classes = 'over-line';
      classes += this.underline ? ' under-line' : '';
      return classes;
    },
  },
};
</script>

<style scoped lang="scss">
@import '@/styles/common.scss';
.over-line {
  position: relative;
  padding-top: 12px;

  &:after {
    background-color: var(--propColor);
    position: absolute;
    display: block;
    content: "";
    width: 40px;
    height: 3px;
    left: 0;
    top: 0;
  }

  &.under-line {
    padding-top: 0;
    padding-bottom: 12px;

    &:after {
      top: auto;
      bottom: 0;
    }
  }
}
</style>

<docs>
OverLine
```vue
    <div style="display: flex; justify-content: space-evenly; align-items: center; background-color: #fff; padding: 15px;">
      <OverLine>
        <h3>Dynamic & Async Components</h3>
      </OverLine>
      <OverLine color="#0984e3">
        <h3>Dynamic & Async Components</h3>
      </OverLine>
    </div>
```
Under
```vue
    <div style="display: flex; justify-content: space-evenly; align-items: center; background-color: #fff; padding: 15px;">
      <OverLine :underline="true">
        <h3>Dynamic & Async Components</h3>
      </OverLine>
      <OverLine :underline="true" color="#0984e3">
        <h3>Dynamic & Async Components</h3>
      </OverLine>
    </div>
```
</docs>