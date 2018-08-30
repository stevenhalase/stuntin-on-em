<template>
  <div :class="classes">
    {{text}}
  </div>
</template>

<script>
/**
 * Option component
 */
export default {
  name: 'Option',
  props: {
    text: {
      type: String,
      required: true,
    },
    selected: {
      type: Boolean,
    },
  },
  computed: {
    classes() {
      let classes = 'option';
      classes += this.selected ? ' selected' : '';
      return classes;
    },
  }
};
</script>

<style scoped lang="scss">
@import '@/styles/common.scss';
.option {
  width: 100%;
  padding: 5px 12px;

  &:hover {
    background-color: $primary_light;
  }
}
</style>

<docs>
```vue
    <div style="display: flex; align-items: center; background-color: #fff; padding: 15px;">
      <Option text="Lucy"/>
    </div>
```
</docs>