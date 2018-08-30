<template>
  <div :class="classes" :style="{ width }">
    <div v-if="!!this.$slots['card-header']" class="card-header">
      <slot name="card-header" />
    </div>
    <div v-if="!!this.$slots['card-content']"  class="card-content">
      <slot name="card-content" />
    </div>
    <div v-if="!!this.$slots['card-footer']"  class="card-footer">
      <slot name="card-footer" />
    </div>
  </div>
</template>

<script>
/**
 * Card component
 */
export default {
  name: 'Card',
  props: {
    /**
    * Card width
    * `'350px'`
    */
    width: {
      type: String,
      default: '350px'
    },
    /**
    * Card border toggle
    * `true, false`
    */
    bordered: {
      type: Boolean,
      default: true,
    },
    /**
    * Card shadow toggle
    * `true, false`
    */
    shadowed: {
      type: Boolean,
    },
    /**
    * Card rounded toggle
    * `true, false`
    */
    rounded: {
      type: Boolean,
    },
  },
  computed: {
    classes() {
      let classes = 'card';
      classes += this.bordered ? ' bordered' : '';
      classes += this.shadowed ? ' shadowed' : '';
      classes += this.rounded ? ' rounded' : '';
      return classes;
    },
  },
}
</script>

<style scoped lang="scss">
@import '@/styles/common.scss';
.card {
  background-color: $white;
  box-sizing: content-box;

  &.bordered {
    border: 1px solid rgba(0,0,0,0.1);
  }

  &.shadowed {
    box-shadow: $shadow;
  }

  &.rounded {
    border-radius: $radius;
  }

  .card-header {
    padding: $padding;
    border-bottom: 1px solid rgba(0,0,0,0.1);
  }

  .card-footer {
    padding: $padding;
    border-top: 1px solid rgba(0,0,0,0.1);
  }
}
</style>

<docs>
```vue
    <div style="display: flex; justify-content: flex-start; align-items: center; width: 100%; overflow-x: auto;">
      <div style="display: flex; justify-content: center; align-items: center; background-color: #2C3741; padding: 15px; width: 50%">
        <Card :bordered="false">
          <template slot="card-header">
            <h3>Card Title</h3>
          </template>
          <template slot="card-content">
            <div 
              style="background: url('https://placeimg.com/800/200/any'); background-size: cover; background-position: center; width: 100%; height: 200px;" />
            <div style="padding: 15px; max-width: 600px;">
              <h3>Dynamic & Async Components</h3>
              <p>
                You’ll notice that if you select a post, switch to the Archive tab, 
                then switch back to Posts, it’s no longer showing the post you selected. 
                That’s because each time you switch to a new tab, Vue creates a new 
                instance of the currentTabComponent.
              </p>
            </div>
          </template>
          <template slot="card-footer">
            <Button text="Learn More" type="primary" :outline="true"/>
          </template>
        </Card>
      </div>

      <div style="display: flex; justify-content: center; align-items: center; background-color: #2C3741; padding: 15px; width: 50%">
        <Card :bordered="false" :rounded="true">
          <template slot="card-header">
            <h3>Card Title</h3>
          </template>
          <template slot="card-content">
            <div 
              style="background: url('https://placeimg.com/800/200/any'); background-size: cover; background-position: center; width: 100%; height: 200px;" />
            <div style="padding: 15px; max-width: 600px;">
              <h3>Dynamic & Async Components</h3>
              <p>
                You’ll notice that if you select a post, switch to the Archive tab, 
                then switch back to Posts, it’s no longer showing the post you selected. 
                That’s because each time you switch to a new tab, Vue creates a new 
                instance of the currentTabComponent.
              </p>
            </div>
          </template>
          <template slot="card-footer">
            <Button text="Learn More" type="primary" :outline="true"/>
          </template>
        </Card>
      </div>

      <div style="display: flex; justify-content: center; align-items: center; background-color: #fff; padding: 15px; width: 50%">
        <Card>
          <template slot="card-header">
            <h3>Card Title</h3>
          </template>
          <template slot="card-content">
            <div 
              style="background: url('https://placeimg.com/800/200/any'); background-size: cover; background-position: center; width: 100%; height: 200px;" />
            <div style="padding: 15px; max-width: 600px;">
              <h3>Dynamic & Async Components</h3>
              <p>
                You’ll notice that if you select a post, switch to the Archive tab, 
                then switch back to Posts, it’s no longer showing the post you selected. 
                That’s because each time you switch to a new tab, Vue creates a new 
                instance of the currentTabComponent.
              </p>
            </div>
          </template>
          <template slot="card-footer">
            <Button text="Learn More" type="primary" :outline="true"/>
          </template>
        </Card>
      </div>

      <div style="display: flex; justify-content: center; align-items: center; background-color: #fff; padding: 15px; width: 50%">
        <Card :bordered="false" :shadowed="true">
          <template slot="card-header">
            <h3>Card Title</h3>
          </template>
          <template slot="card-content">
            <div 
              style="background: url('https://placeimg.com/800/200/any'); background-size: cover; background-position: center; width: 100%; height: 200px;" />
            <div style="padding: 15px; max-width: 600px;">
              <h3>Dynamic & Async Components</h3>
              <p>
                You’ll notice that if you select a post, switch to the Archive tab, 
                then switch back to Posts, it’s no longer showing the post you selected. 
                That’s because each time you switch to a new tab, Vue creates a new 
                instance of the currentTabComponent.
              </p>
            </div>
          </template>
          <template slot="card-footer">
            <Button text="Learn More" type="primary" :outline="true"/>
          </template>
        </Card>
      </div>
    </div>
```
</docs>