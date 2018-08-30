<template>
  <div :class="classes">
    <router-link :to="to">{{ formattedName }}</router-link>
  </div>
</template>

<script>
/**
 * NavItem component
 */
export default {
  name: 'NavItem',
  props: {
    /**
    * The route to link to
    * `'/example'`
    */
    to: {
      type: String,
    },
    /**
    * The text for the button
    * `'Example'`
    */
    name: {
      type: String,
      required: true,
    },
    /**
    * Whether this element is active
    * `true, false`
    */
    active: {
      type: Boolean,
    },
  },
  computed: {
    classes() {
      let classes = 'nav-item';
      classes += this.active ? ' active' : '';
      return classes;
    },
    formattedName() {
      return this.name.toUpperCase();
    },
  },
};
</script>

<style scoped lang="scss">
@import '@/styles/common.scss';
.nav-item {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: $white;
  padding: 0px $padding;
  height: 80px;
  color: $black;
  font-weight: 700;
  font-size: 13px;
  border-bottom: 3px solid transparent;

  &.active {
    border-bottom: 3px solid $primary;
    cursor: default;
    pointer-events: none;
  }

  &:hover {
    border-bottom: 3px solid $primary;
    cursor: pointer;
  }
}
</style>

<docs>
```vue
    <div style="display: flex; align-items: center; background-color: #2C3741; padding: 15px;">
      <NavItem to="/example" name="home" :active="true"/>
      <NavItem to="/example" name="about"/>
    </div>
```
</docs>