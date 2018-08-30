<template>
  <div :class="classes">
    <div class="modal-content">
      <Button
        @click.native="closeModal"
        type="secondary"
        icon="times"
        :circle="true" />
      <slot></slot>
    </div>
    <div 
      @click="closeModal"
      class="modal-backdrop" />
  </div>
</template>

<script>
import Button from '@/components/ui/Button.vue';
/**
 * Modal component
 */
export default {
  name: 'Modal',
  data() {
    return {
      open: false
    }
  },
  computed: {
    classes() {
      let classes = 'modal';
      classes += this.open ? ' open' : '';
      return classes;
    },
  },
  methods: {
    /**
    * Opens the modal
    * @public
    */
    openModal() {
      this.open = true;
    },
    /**
    * Closes the modal
    * @public
    */
    closeModal() {
      this.open = false;
    }
  },
  components: {
    Button,
  },
};
</script>

<style scoped lang="scss">
@import '@/styles/common.scss';
.modal {
  display: none;
  width: 100vw;
  height: 100vh;
  position: fixed;
  left: 0;
  top: 0;
  z-index: 100;

  &.open {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal-content {
    min-width: 400px;
    min-height: 400px;
    max-width: 80vw;
    max-height: 80vh;
    background-color: $white;
    border-radius: $radius;
    z-index: 101;
    position: relative;

    .button {
      position: absolute;
      right: -30px;
      top: -20px;
    }
  }

  .modal-backdrop {
    width: 100vw;
    height: 100vh;
    position: fixed;
    left: 0;
    top: 0;
    background-color: rgba(0,0,0,0.7);
  }
}
</style>

<docs>
```js
new Vue({
  methods: {
    openModal() {
      this.$refs.modal.openModal();
    },
  },
  template: `
    <div>
      <Button text="Open Modal" @click.native="openModal" />
      <Modal ref="modal">
        <Card :bordered="false" :rounded="true" :shadowed="true" width="400px">
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
      </Modal>
    </div>
  `
})
```
</docs>