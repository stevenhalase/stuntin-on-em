<template>
  <div class="nav">
    <NavItem to="/" name="home" :active="true"/>
    <NavItem to="/about" name="about"/>
    <NavItem to="/services" name="services"/>
    <Action text="Contact Us"/>
  </div>
</template>

<script>
import NavItem from '@/components/Nav/NavItem.vue';
import Action from '@/components/Action/Action.vue';
/**
 * Main Nav component
 */
export default {
  name: 'Nav',
  components: {
    NavItem,
    Action,
  },
};
</script>

<style scoped lang="scss">
@import '@/styles/common.scss';
.nav {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 80px;
  background-color: $white;
  min-width: 400px;
  border-radius: $radius;
  box-shadow: 0px -8px 0px 0px rgba(255,255,255,0.2);
}
</style>

<docs>
```vue
    <div style="display: flex; align-items: center; background-color: #2C3741; padding: 15px;">
      <Nav />
    </div>
```
</docs>